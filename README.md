# sequelize-postgres-manual
Something like a proper cheatsheet for Sequelize.js and PostgreSQL.

# Initial Steps
First of all we need to install the proper packages for sequelize and postgres

For testing purposes there should also be a local PostgreSQL installation ready to go.

# Installation
```bash
npm install --save pg pg-hstore sequelize sequelize-cli
```
#Bootstrapping
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
