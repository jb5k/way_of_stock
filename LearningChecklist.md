# Learning Checklist

This document is meant to outline a pathway to learn the basics about the stocksoftware specific tools
and processes we use day to day.

# Stage 1

* Define Simple Buildr project:
    * Ensure ruby environment for project is configured.
    * Package a basic war file.
    * JAX-RS endpoint that uses a simple CDI service to emit hello world.
    * Use testng to test service.

* Define `setup.sh` for local glassfish

* Define project on Jenkins without deploying to Development
    * Define `ci:package` task in buildr.

# Stage 2

* Define chef infrastructure for project:
    * Define a single glassfish template.
    * Define an application data bag item.

* Enhance Jenkins job definition to include a "Deploy to Development" job.

* Observe application deployed in Sauron

# Stage 3

* Use domgen to define service interface:
    * Braid in domgen.
    * Define project in `architecture.rb`.
    * Enable `ejb` facet in domgen repository.
    * Configure domgen buildr tasks to generate source.
    * Replace service interface with domgen defined service.
    * Use domgen generated base ejb test for service.

# Stage 4

* Use dbt to define automate database creation:
    * Braid in dbt.
    * Enable `mssql` facet in domgen repository.
    * Configure dbt buildr tasks to create database.
    * Configure domgen buildr tasks to generate database sql.
    * Setup template files for database configuration.
    * Generate `db` project that generates db jar.
* Use domgen to define entity/table in database:
    * Enable `jpa` facet in domgen repository.
    * Update `setup.sh` script to configure databases.
    * Define a single entity in domgen repository.
    * Configure domgen buildr tasks to generate source for jpa entities and jpa base test classes.
* Update chef infrastructure for project:
    * Define a single database template.
    * Update application data bag item to deploy database.

* Observe application deployed in Sauron

# Stage 5

* Integrate Checkstyle into Buildr.
* Integrate PMD into Buildr.
* Integrate Findbugs into Buildr.
* Define `ci:commit` task.
* Update Jenkins to add commit job.
