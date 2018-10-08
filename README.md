# sequelize-postgres-manual
Something like a proper cheatsheet for Sequelize.js and PostgreSQL.

# Initial Steps
First of all we need to install the proper packages for sequelize and postgres

For testing purposes there should also be a local PostgreSQL installation ready to go.

# Installation
```bash
npm install --save pg pg-hstore sequelize sequelize-cli
```
## Bootstrapping
To create an empty project you will need to execute init command
```bash
node_modules/.bin/sequelize init
```
This will create following folders

config, contains config file, which tells CLI how to connect with database
models, contains all models for your project
migrations, contains all migration files
seeders, contains all seed files

## Configuration
Before continuing further we will need to tell CLI how to connect to database. To do that let's open default config file config/config.json. It looks something like this
```json
{
  "development": {
    "username": "root",
    "password": null,
    "database": "database_development",
    "host": "127.0.0.1",
    "dialect": "mysql"
  },
  "test": {
    "username": "root",
    "password": null,
    "database": "database_test",
    "host": "127.0.0.1",
    "dialect": "mysql"
  },
  "production": {
    "username": "root",
    "password": null,
    "database": "database_test",
    "host": "127.0.0.1",
    "dialect": "mysql"
  }
}
```
# A little bit of theory
Now there is some explaining to be done before procceeding to the next section

## Seeders,Models and Migrations
### Models
A Model represents a table in the database.

### Migrations
Schema migration (also database migration) refers to the management of incremental, reversible changes to relational database schemas. A schema migration is performed on a database whenever it is necessary to update or revert that database's schema to some newer or older version.

Migrations are performed programmatically by using a schema migration tool. When invoked with a specified desired schema version, the tool automates the successive application or reversal of an appropriate sequence of schema changes until it is brought to the desired state.

Most schema migration tools aim to minimize the impact of schema changes on any existing data in the database. Despite this, preservation of data in general is not guaranteed because schema changes such as the deletion of a database column can destroy data (i.e. all values stored under that column for all rows in that table are deleted). Instead, the tools help to preserve the meaning of the data or to reorganize existing data to meet new requirements. Since meaning of the data often cannot be encoded, the configuration of the tools usually needs manual intervention.

### Seeders
Database Seeding is the initial seeding of a database with data.
Seeding a database is a process in which an initial set of data is provided to a database when it is being installed .
It is especially useful when we want to populate the database with data we want to develop in future.
This is often an automated process that is executed upon the initial setup of an application.

## Sequelize Models Seeders and Migrations
Now it's time for some details
### Sequelize Migrations
Each migration manipulates database tables. The definition of this table has to include all columns including "id" and even the optional "createdAt" and "updatedAt" along with any other foreign key definition and its reference and constraints.
### Sequelize Models
No foreign keys are declared in models. Instead, associations are used. Associations are used to declare connections on foreign keys with other tables along with their reference key and their association type (1:1,1:n,n:n)

####Important note!
When defining associations we should always take into considerations the access type that we would like to have in our tables.
There are the one-way associtiations and the two-way associations. This has to do with how you want to access your models.
If for example we have a User model and a Post model, if we declare this as a one-way association ( User has many Post) then we will not be able to query from Posts to get User specific data.

Usually all associations are declared as two-way unless there is a specific design restriction.

### Sequelize Seeders
They are similar to migrations in structure but they are only used to populate initial required data.

