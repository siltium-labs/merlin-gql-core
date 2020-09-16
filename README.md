[![oclif](https://img.shields.io/badge/cli-oclif-brightgreen.svg)](https://oclif.io)
[![Version](https://img.shields.io/npm/v/merlin-gql.svg)](https://npmjs.org/package/merlin-gql)
[![Downloads/week](https://img.shields.io/npm/dw/merlin-gql.svg)](https://npmjs.org/package/merlin-gql)
[![License](https://img.shields.io/npm/l/merlin-gql.svg)](https://github.com/ezequielzacca/merlin-gql/blob/master/package.json)

Merlin GQL
==========

**Merlin GQL** is a framework to create Graphql APIs using ***Typescript***, ***TypeORM*** and ***TypeGraphQL*** whose aim is to make developing database oriented GraphQL APIs as simple and straightforward as possible without making compromises on customization or extensibility of your APIs.

We simplify common use cases with out of the box features that help developers to simplify and speed up the development of GraphQL APIs.

## Features
  
 
### Code Generation
Merlin GQL has a cli that will generate pretty much everything you need to make a functional GraphQL API.

You can develop your API using two approaches, both are covered in the **TypeORM Entities** section of the documentation

- Database First (reverse engineering an existing database)
- Code First (creating your database entities in the code and synchronizing your database schema with your code)

You can switch from one to the other at *any point* and starting with either *doesn't lock you* into using that strategy through the rest of the development cycle of your API.

### Templates

Using the CLI you can create the basic structure of your API and you can select between a *basic* and an *example* template, which will showcase and provide example code for all of the features included in Merlin GQL plus some examples of customizations that you might find usefull later. We encourage to select our example template as a guide and starting point if this is the first time using this framework.

### Authentication and Authorization

This is a very common feature needed in the majority of cases when creating an API, so we decided to provide out of the box features to secure your APIs, this approach is very simple and may not be suitable for all cases, but you can customize it, extend it or completely ignore it and create your own security layer.

For more information on this feature please refer to the **Authentication and Authorization** section of the documentation.

### Data Generation

We provide some simple tools and guidelines for automatically generating testing data for your API, this step is often overlooked and will help you to create "fake" data in order to have some interesting data for your tests, measure performance, put your API in stress or simply provide a starting point for the developer and avoid an empty database.

## Getting Started

To start with Merlin GQL, we strongly recommend to install our CLI, you might find it really usefull and it will speed up your development, altough *it is not required*.

### CLI Installation

You can use *npx* or install it globally with *npm*, both approaches are valid and will work without any kind of problems.

If you want to install Merlin GQL globally with npm you need to run the command:

```
npm install --global merlin-gql
```
or it's short version
```
npm i -g merlin-gql
```

If you want to use *npx* instead, you don't need to install Merlin GQL globally.


>From now on and through the rest of the guide, we will assume that you have the CLI installed globally, if you decided to use *npx* then all you need to do is to prefix all the commands with `npx `.


### Starting a new project
With the CLI you can create a new project using the *new* command

```
merlin-gql new
```
or with npx
```
npx merlin-gql new
```

Once you run the command, the CLI will guide ask you to choose a template for your project, if you are familiar with Merlin GQL you can select the **Bascic** template, which is a template with only the bare minimum files required to create your API without any example files and without boilerplate code. 

As previously recommended, if this is your first time using Merlin GQL or you want to explore it's features, we recommend to select the **Example** template.

#### Example Template

The first thing the CLI will ask you for, is the *name* of your project.

![Imgur](https://i.imgur.com/JojUxbU.png)





  
  <details>
    <summary>Templates</summary>
  </details>
  <details>
    <summary>Authentication & Authorization</summary>
  </details>
  <details>
    <summary>
      CRUD (with Queries, Mutations and Subscriptions)
    </summary>
  </details>
  <details>
    <summary>
      Data Generation (for testing or debbuging purposes)
    </summary>
  </details>


### CLI
<!-- toc -->
* [Usage](#usage)
* [Commands](#commands)
<!-- tocstop -->


# Usage
<!-- usage -->
```sh-session
$ npm install -g merlin-gql
$ merlin-gql COMMAND
running command...
$ merlin-gql (-v|--version|version)
merlin-gql/0.2.13 win32-x64 node-v10.15.0
$ merlin-gql --help [COMMAND]
USAGE
  $ merlin-gql COMMAND
...
```
<!-- usagestop -->

# Commands
<!-- commands -->
* [`merlin-gql db-reverse`](#merlin-gql-db-reverse)
* [`merlin-gql generate:crud`](#merlin-gql-generatecrud)
* [`merlin-gql generate:entity`](#merlin-gql-generateentity)
* [`merlin-gql help [COMMAND]`](#merlin-gql-help-command)
* [`merlin-gql list:entities`](#merlin-gql-listentities)
* [`merlin-gql new`](#merlin-gql-new)

## `merlin-gql db-reverse`

generate models and graphql resolvers with database reverse engineering.

```
USAGE
  $ merlin-gql db-reverse

OPTIONS
  -d, --database=database                                  Database name(or path for sqlite). You can pass multiple
                                                           values separated by comma.

  -e, --engine=mssql|postgres|mysql|mariadb|oracle|sqlite  Database engine

  -h, --host=host                                          IP address/Hostname for database server

  -o, --output=output                                      Where to place generated models

  -p, --port=port                                          Port number for database server

  -s, --schema=schema                                      Schema name to create model from. Only for mssql and
                                                           postgres. You can pass multiple values separated by comma eg.
                                                           -s scheme1,scheme2,scheme3

  -u, --user=user                                          Username for database server

  -x, --pass=pass                                          Password for database server

  --ce=pascal|camel|none                                   Convert class names to specified case

  --cf=pascal|param|camel|none                             Convert file names to specified case

  --cp=pascal|camel|snake|none                             Convert property names to specified case

  --defaultExport                                          Generate index file

  --disablePluralization                                   Disable pluralization of OneToMany, ManyToMany relation names

  --eol=LF|CRLF                                            Force EOL to be LF or CRLF

  --generateConstructor                                    Generate constructor allowing partial initialization

  --help                                                   show CLI help

  --lazy                                                   Generate lazy relations

  --namingStrategy=namingStrategy                          Use custom naming strategy

  --noConfig                                               Doesn't create tsconfig.json and ormconfig.json

  --pv=public|protected|private|none                       Defines which visibility should have the generated property

  --relationIds                                            Generate RelationId fields

  --secureResolvers                                        Add security to Resolvers with @Secure decorator

  --skipSchema                                             Omits schema identifier in generated entities

  --skipTables=skipTables                                  Skip schema generation for specific tables. You can pass
                                                           multiple values separated by comma

  --ssl                                                    Use ssl connection

  --strictMode=none|?|!                                    Mark fields as optional(?) or non-null(!)

DESCRIPTION
  Usage: merlin-gql db-reverse -h <host> -d <database> -p [port] -u <user> -x [password] -e [engine]

     You can also run program without specifying any parameters to launch interactive mode.
```

_See code: [src\commands\db-reverse.ts](https://github.com/silentium-labs/merlin-gql-cli/blob/v0.2.13/src\commands\db-reverse.ts)_

## `merlin-gql generate:crud`

Generate input, filter, sort GraphQL models and GraphQL resolvers from entity models.

```
USAGE
  $ merlin-gql generate:crud

OPTIONS
  -f, --filter    Generate filter GraphQL model from entity model
  -i, --input     Generate input GraphQL model from entity model
  -r, --resolver  Generate GraphQL resolver from entity model
  -s, --sort      Generate sort GraphQL model from entity model
  --help          show CLI help

DESCRIPTION
  Usage: merlin-gql generate:crud -i -f -s -r

       You can also run program without specifying any parameters to launch interactive mode.

EXAMPLE
  $ merlin-gql generate:crud
```

_See code: [src\commands\generate\crud.ts](https://github.com/silentium-labs/merlin-gql-cli/blob/v0.2.13/src\commands\generate\crud.ts)_

## `merlin-gql generate:entity`

Allows code generation

```
USAGE
  $ merlin-gql generate:entity

OPTIONS
  -n, --name=name
  -r, --resolver

ALIASES
  $ merlin-gql g:e

EXAMPLE
  $ merlin-gql generate:entity
```

_See code: [src\commands\generate\entity.ts](https://github.com/silentium-labs/merlin-gql-cli/blob/v0.2.13/src\commands\generate\entity.ts)_

## `merlin-gql help [COMMAND]`

display help for merlin-gql

```
USAGE
  $ merlin-gql help [COMMAND]

ARGUMENTS
  COMMAND  command to show help for

OPTIONS
  --all  see all commands in CLI
```

_See code: [@oclif/plugin-help](https://github.com/oclif/plugin-help/blob/v3.1.0/src\commands\help.ts)_

## `merlin-gql list:entities`

Lists all typeorm existing entities

```
USAGE
  $ merlin-gql list:entities

ALIASES
  $ merlin-gql l

EXAMPLE
  $ merlin-gql list:entities
```

_See code: [src\commands\list\entities.ts](https://github.com/silentium-labs/merlin-gql-cli/blob/v0.2.13/src\commands\list\entities.ts)_

## `merlin-gql new`

creates a new merlin-gql project.

```
USAGE
  $ merlin-gql new

OPTIONS
  -d, --databaseName=databaseName          Database Name
  -h, --databaseHost=databaseHost          Database Host
  -n, --name=name                          Name of the project
  -p, --databasePassword=databasePassword  Database Password
  -p, --databasePort=databasePort          Database Port
  -s, --jwtSecretToken=jwtSecretToken      Secret JWT Encryption Token
  -t, --databaseType=databaseType          Database Type
  -t, --template=basic|example             Template
  -u, --databaseUser=databaseUser          Database User
  --help                                   show CLI help
  --ngrok                                  Enable ngrok for remote testing

DESCRIPTION
  Usage: merlin-gql new -t example -n myProject

     You can also run program without specifying any parameters to launch interactive mode.

ALIASES
  $ merlin-gql new
```

_See code: [src\commands\new.ts](https://github.com/silentium-labs/merlin-gql-cli/blob/v0.2.13/src\commands\new.ts)_
<!-- commandsstop -->
