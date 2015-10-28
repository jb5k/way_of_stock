# Release Process

Each application (or service) has a slightly different release process. The release process may require approval from
the business owner and may require additional steps that are not yet automated (such as uploading reports
to SQL Server Reports Server). However this document attempts to document the common aspects of the release
process.

## Concepts

Each application requires releases of multiple _facets_. For example a release may involve:

* Creating or migrating a database.
* Adding or updating destinations on a message broker.
* Deploying a ``.war`` file (or other deployable unit) to [GlassFish](InstallGlassFish.md).
* Updating the monitoring system with new checks and probes etc.
* Updating load balancer with new routes.

Each of these are represented by a separate _facet_. The ``dbt`` facet is responsible for updating the database
server, the ``openmq`` facet is responsible for updating the message broker, the ``glassfish`` facet updates the
GlassFish domain(s) and the ``monitor`` facet updates the monitoring system, etc.

The applications are released using the [Chef](http://chef.io) system automation framework. We describe each
application using a series of recipes and databags.

The application is primarily defined in an application data bag item in the ``applications`` data bag. The data bag
item typically defines an object literal for each _facet_, a bag of application specific configuration under the key
``config`` as well as the following top level keys.

* *id*: A unique ID for the data bag that matches the file name. By convention we use "*type*_*chef_environment*".
* *type*: Unique key for the application.
* *chef_environment*: The chef environment in which application instance is deployed.
* *nodes*: An array of strings indicating the nodes and order in which the nodes are converged during a release.
Note: This is only required due to inability of release process to determine these nodes automatically and this
requirement may be removed in a future release.
* *enabled*: A flag set to true to indicate application should be deployed. If this key is not set, then the
release process defaults it to true.

An example of an application data bag:

```json
{
  "id": "myapp_development",
  "type": "myapp",
  "chef_environment": "development",
  "nodes": [
    "DEVmq.example.com",
    "DEVsql.example.com",
    "DEVappserver.example.com"
  ],
  "enabled": "true",
  "monitor": {
    "template_version": "2"
  },
  "glassfish": {
    "domain": "appserver",
    "template_version": "6"
  },
  "openmq": {
    "template_version": "5"
  },
  "dbt": {
    "priority": 40,
    "instance_key": "appsdb",
    "database_key": "MYAPP",
    "major_version": 3,
    "enforce_version_match": true,
    "username": "myapp_rw",
    "password": "myapp_password",
    "template_version": "3",
    "import_on_create": true
  },
  "config": {
    "plugin": "myapp-extender"
  }
}
```

## Templates

Templates are used as way of abstracting and reusing a chunk of configuration across multiple applications,
environments or nodes. Consider the scenario where a application is deployed to multiple environments; development,
uat, training and production. This application is likely to have similar glassfish configurations in each environment.
In this scenario the common configuration could be abstracted out into a template. The _facet_ configuration in the
``applications`` data bag item for the application would then reference the template.

Templates are stored in the ``templates`` data bag and must have the following top level keys.

* *id*: A unique ID for the data bag that matches the file name. By convention we use "*template_type*_*application*_*version*".
* *application*: Unique key for the application.
* *template_type*: A key identifying the _type_ of the template, usually the same name as the associated facet.
* *version*: A unique key within the scope of *application* and *template_type* that identifies a particular version
of the template. This is usually a monotonically increasing number.

The templates also have 1 or more additional top level keys that contain the shared configuration. These subkeys
are defined by the template type.

```json
{
  "id": "glassfish_myapp_v6",
  "application": "myapp",
  "template_type": "glassfish",
  "version": "6",
  "config": {
    ...
  }
}
```

Each facet within the application instance identifies which templates to use based on the presence of the top level
``type`` key and the sub-key ``template_version`` in the facet configuration. Consider the following application
configuration which would load the above template named ``glassfish_myapp_v6``.

```json
{
  ...
  "type": "myapp",
  ...
  "glassfish": {
    "template_version": "6",
    ...
  },
  ...
}
```

Note: There are some scenarios where a template is not associated with an application or a facet but we have not
settled on a concrete pattern by which we select the templates and versions to retrieve configuration from. An
example of this is the domain _template type_ that can be blended into a GlassFish domain based on a hash that
maps "application" keys to versions.

### GlassFish Template

The GlassFish templates are used by applications and require referencing from application instances.

#### Facet Configuration

The facet should include the following additional keys:

* *domain*: This specifies a symbolic key identifying which particular glassfish domain the application should be installed.

The configuration of the facet should look something like:

```json
{
  ...
  "type": "myapp",
  ...
  "glassfish": {
    "domain": "mydomain",
    "template_version": "6"
  },
  ...
}
```

#### Template Structure

The template has a single additional top level element named ``config`` that contains a chunk of configuration
that is blended into the configuration of the domain. The structure of this configuration is not described anywhere
and you will need to look at the existing examples for inspiration. However there are a few important sections that
are common across our applications.

Firstly most applications should define a deployable with a name that matches the name of the application type. While
not strictly required this avoids the need to specify additional parameters at later steps. The template should also
define a url for the deployable that may include the symbol ``$VERSION`` that is replaced with the actual version of
the application when the template is blended into domain configuration. It is also highly likely that you need to
define a _before_ hook that specifies a recipe to run prior to attempting to deploy the application. This allows
the developer to write some basic ruby code that can customize the deploy for the application.

A sample template that includes the minimal configuration is:

```json
{
  "id": "glassfish_myapp_v6",
  "application": "myapp",
  "template_type": "glassfish",
  "version": "6",
  "config": {
    "recipes": {
      "before": {
        "mycookbook::myapp_v6": {}
      }
    },
    "deployables": {
      "myapp": {
        "url": "http://repo.example.com/releases/myapp/myapp/$VERSION/myapp-$VERSION.war",
        "context_root": "/myapp"
      }
    }
  }
}
```

A minimal recipe ``myapp_v6`` added to the ``mycookbook`` cookbook should look something like:

```ruby
RealityForge::Application.load_application_data(node, 'myapp')
RealityForge::GlassFish.define_base_deployable(node, 'myapp')
```

However most applications perform other configuration such as configuration of jdbc, mail or jms resources. Look
at the existing recipes for inspiration.

### Dbt Template

TODO

### OpenMQ Template

OpenMQ is the message broker in use and this OpenMQ template is used as an application facet. The template/facet
allows you to declare queues, topics, access_rules and accounts to be added to the message broker.

#### Facet Configuration

The template requires no additional configuration other than the ``template_version`` key. For example:

```json
{
  ...
  "type": "myapp",
  ...
  "openmq": {
    "template_version": "6"
  },
  ...
}
```

#### Template Structure

TODO

### Monitor Template

The monitor template is the template used by our monitoring system (Sauron) to determine how to publish
the endpoints that need to be monitored. It is an application facet.

#### Facet Configuration

The template requires no additional configuration other than the ``template_version`` key. For example:

```json
{
  ...
  "type": "myapp",
  ...
  "monitor": {
    "template_version": "3"
  },
  ...
}
```

#### Template Structure

TODO

### Domain Template

TODO
