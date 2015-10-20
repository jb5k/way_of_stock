# Release Process

Each application (or service) has a slightly different release process. The release process may require approval from
the business owner and may require additional steps that are not yet automated (such as uploading reports
to SQL Server Reports Server). However this document attempts to document the common aspects of the release
process.

## Concepts

Each application requires releases of multiple _facets_. For eaxmple a release may involve:

* Creating or migrating a database.
* Adding or updating destinations on a message broker.
* Deploying a ``.war`` file (or other deployable unit) to [GlassFish](InstallGlassFish.md).
* Updating the monitoring system with new checks and probes etc.

Each of these are represented by a separate _facet_. The ``dbt`` facet is responsible for updating the database
server, the ``openmq`` facet is responsible for updating the message broker, the ``glassfish`` facet updates the
GlassFish domain(s) and the ``monitor`` facet updates the monitoring system.

The applications are released using the [Chef](http://chef.io) system automation framework. We describe each
application using a series of recipes and databags.

The application is primarily defined in an application data bag item in the ``applications`` data bag. The data bag
item typically defines an object literal for each _facet_, an bag of application specific configuration under the key
``config`` as well as the following top level keys.

* *id*: A unique ID for the data bag that matches the file name. By convention we use "*type*_*chef_environment*".
* *type*: Unique key for the application.
* *chef_environment*: The chef environment in which application instance is deployed.
* *nodes*: An array of strings indicating the nodes and order in which the nodes are converged during a release.
Note: This is only required due to inability of release process to determine these nodes automatically. 
* *enabled*: A flag set to true to indicate application should be deployed. If this key is not set, then the
release process defaults it to true.

An example of an application data bag

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

TODO: templates, template types

### GlassFish Template

TODO

### Dbt Template

TODO

### OpenMQ Template

TODO

### Monitor Template

TODO
