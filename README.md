# sfdx-djc-plugin  [![Build Status](https://travis-ci.org/dcarroll/sfdx-djc-plugin.svg?branch=master)](https://travis-ci.org/dcarroll/sfdx-djc-plugin)<!-- tocstop -->

[![Version](https://img.shields.io/npm/v/datatree.svg)](https://npmjs.org/package/sfdx-djc-plugin)
[![License](https://img.shields.io/npm/l/datatree.svg)](https://github.com/dcarroll/sfdx-djc-plugin/blob/master/package.json)


<!-- toc -->

<!-- install -->
A plugin for the Salesforce CLI built by Dave Carroll and containing a few of helpful commands.

## Setup

### Install from source

1. Install the SDFX CLI.

2. Clone the repository: `git clone git@github.com:wadewegner/sfdx-waw-plugin.git`

3. Install npm modules: `npm install`

4. Link the plugin: `sfdx plugins:link .`

### Install as plugin

1. Install plugin: `sfdx plugins:install sfdx-waw-plugin`

<!-- usage -->
```sh-session
$ npm install -g sfdx
$ sfdx COMMAND
running command...
$ sfdx (-v|--version|version)
sfdx/0.0.0 darwin-x64 node-v9.3.0
$ sfdx --help [COMMAND]
USAGE
  $ sfdx COMMAND
...
```
<!-- usagestop -->
<!-- commands -->
* [`sfdx djc:data:export`](#sfdx-djcdataexport)

## `sfdx djc:data:export`

This is a proof of concept of a entirely differenct way to extract data from an org to use as developer data for a scratch org.  Just supply a list of SObject, standard or custom, and you *should* end up with a dataset and data plan that can be used with the official force:data:tree:import command

```
USAGE
  $ sfdx djc:data:export

OPTIONS
  -m, --maxrecords=maxrecords                     [default: 10] Max number of records to return in any query

  -n, --planname=planname                         [default: new-plan] name of the data plan to produce, deflaults to
                                                  "new-plan"

  -o, --objects=objects                           (required) Comma separated list of objects to fetch

  -t, --targetdir=targetdir                       (required) target directoy to place results in

  -u, --targetusername=targetusername             username or alias for the target org; overrides default target org

  --apiversion=apiversion                         override the api version used for api requests made by this command

  --json                                          format output as json

  --loglevel=(trace|debug|info|warn|error|fatal)  logging level for this command invocation

EXAMPLE
  $ sfdx djc:data:export -o Account,Contact,Case,Opportunity -t data/exported -n my-testplan
  $ sfdx djc:data:export -o "Account, CustomObj__c, OtherCustomObj__c, Junction_Obj__c" - t data/exported
```

_See code: [src/commands/djc/data/export.ts](https://github.com/dcarroll/datatree/blob/v0.0.0/src/commands/djc/data/export.ts)_
<!-- commandsstop -->
