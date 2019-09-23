# ApiFlows CLI
[Back to References](References.md) | [TOC](README.md)


```bash
$ apiflows --help

Usage: apiflows [command] [options]

ApiFlows CLI

Options:
  -V, --version    output the version number
  -h, --help       output usage information

Commands:
  init|i           get credentials from ApiFlows
  user|u           create ,modify, or delete ApiFlows users
  account|a        create ,modify, or delete ApiFlows accounts
  subscription|su  create ,modify, or delete ApiFlows subscriptions
  flow|fl          create ,modify, or delete ApiFlows flows
  context|c        create ,modify, delete, start or stop  ApiFlows contexts
  help [cmd]       display help for [cmd]
```

**WARNING** : user, account and subscription subcommands are not yet available in ApiFlows MVP2.
As a consequence, only flow and context subcommands are documented.

## flow subcommand

```bash
$ apiflows flow --help

Usage: apiflows-flow [command] [options] 

Options:
  -h, --help        output usage information

Commands:
  list              list flows 
  create [options]  create a flow
  get [options]     get a flow description
  modify [options]  modify a flow
  delete [options]  delete a flow
```

#### How to create a flow
```bash
$ apiflows flow create --help

Usage: create [options]

create a flow

Options:
  --file <path>  json file containing description of flow
  -h, --help     output usage information
```
json file contains a json object with following properties : [**Flow**](Flow.md)

#### How to list existing flows
```bash
$ apiflows flow list

list existing flows
```

#### how to get the status of a flow

```bash
$ apiflows flow get --help

Usage: get [options]

get a flow description

Options:
  --flowId <flowId>  flow ID
  -h, --help         output usage information
```
#### how to modify a flow

```bash
$ apiflows flow modify --help


[Back to References](References.md) | [TOC](README.md)