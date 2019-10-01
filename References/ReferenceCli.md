# ApiFlows CLI
[Back to References](../References.md) | [TOC](../README.md)


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
As a consequence, only **flow** and **context** subcommands are documented.

## flow subcommand

```bash
$ apiflows flow --help

Usage: apiflows flow [options] [command]

Options:
  -h, --help        output usage information

Commands:
  list              list flows 
  create [options]  create a flow
  start [options]   start a flow
  get [options]     get a flow description
  modify [options]  modify a flow
  delete [options]  delete a flow
  stop [options]    stop a flow

```

### How to create a flow
```bash
$ apiflows flow create --help

Usage: create [options]

create a flow

Options:
  --flowId <flowId>  flow ID
  -h, --help         output usage information

```
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Example :**
```bash
$ apiflows create --flowId myflow
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**What's done by ApiFlows when creating a Flow**

ApiFlows automatically creates a new single sdk node-RED instance in the cloud , with a graphical editor.
Editor URI is returned by create command
 


### How to list existing flows
```bash
$ apiflows flow list

list existing flows
```

### how to get the status of a flow

```bash
$ apiflows flow get --help

Usage: get [options]

get a flow description

Options:
  --flowId <flowId>  flow ID
  -h, --help         output usage information
```
### how to modify a flow

```bash
$ apiflows flow modify --help

Usage: modify [options]

modify a flow

Options:
  --flowId <flowId>  flow ID
  --file <path>      json file containing the description of the flow
  -h, --help         output usage information
```

json file contains a json object with following properties : [**Flow**](CliFlow.md)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**What's the impact of flow resource modification**


*   If **mode** changes from **sdk** to **multi** : ApiFlows automatically stops  the  sdk single  Node-RED instance. It then creates a set of new Node-RED instances without editor. Depending on other Flow properties, like **autoscale**, **replicas**, **minReplicas**, **maxReplicas**, the number of Node-RED instances, can be fixed or can vary automatically depending on the workload
*   If **mode** changes from **multi** to **sdk** : ApiFlows automatically stops  all the running multi Node-RED instances. It then creates a new single sdk node-RED instance , with a graphical editor reachable on the web.
* if **mode** remains sdk : No impact
* if **mode** remains multi and **autoscale** remains **false** and  **replicas** changes, apiflows scales up or down to the **replicas** number of instances
* if **mode** remains multi and **autoscale** changes to **true**, apiflows start adapting the number of NodeRED instances automatically, based on workload . The minimum NodeRED instances will depend on **minReplicas** propery while the maximum NodeRED instances will be set by **maxReplicas** property

Example of flow lifecycle :

T0 : $ apiflows flow create --flowId myflow
T1 : $ apiflows flow modify --flowId myflow --file 


## context subcommand

```bash
$ apiflows context --help

Usage: apiflows context [options] [command]

Options:
  -h, --help        output usage information

Commands:
  list [options]    list contexts 
  create [options]  create a group of context
  get [options]     get a context description
  start [options]   start contexts
  stop [options]    stop contexts
  delete [options]  delete contexts
  modify [options]  modify contexts
  ```
### How to create (and inject )contexts

```bash
$ apiflows context create --help

Usage: create [options]

create a group of context

Options:
  --flowId [flowId]    flow ID
  --nb <nb>            number of context to create
  --groupId [groupId]  group ID
  --start              start context after creation
  --wireIn [wireIn]    wire-in entry in which context must be started. Mandatory if --start is defined
  --file <path>        json file containing description of context
  -h, --help           output usage information
  ```

  * **flowId** is mandatory. Contexts are created in the context of a flowId
  * **nb** is the number of contexts to create
  * **groupId** is the group to which contexts will belong in the scope of the flowId. It enables to discriminate contexts, in case we would like to modify or stop  a part of them. ( see stop , start, modify, delete )
  * **json file** contains a description of context(s) to create. Here is a description of contexts json object : [Context](Context.md). If **groupId** is not defined, **contextId** is a mandatory property of the  Context object. In that case, ApiFlows creates only one Context with ID **contextId**. If **groupId** is defined, **contextId** must not be defined in context Object. In that case, ApiFlows creates **nb** contexts, with a generated ID, prefixed with  **groupId**, and suffixed with a number.
  
  * if **--start** option is used, contexts are not only created, but also injected in ApiFlows messaging network.
  As a consequence, they must be addressed to a **wire-in** 
  node, using its **pin_name** address. Option **--wireIn** is mandatory and must target the **pin_name** of one **wire-in** node of the flow.

  ### How to list contexts

```bash
$ apiflows context list --help
Usage: list [options]

list contexts 

Options:
  --flowId [flowId]    flow ID
  --groupId [groupId]  group ID
  -h, --help           output usage information
  ```

  * **flowId** is mandatory and define the flowId to which context(s) belongs to
  * if **groupId** is not defined, all contexts created in the scope of **flowId** are listed
  * if **groupId** is defined, a summary of the contexts created in the scope of **flowId** with this particular **groupId**, is made.

### How to get the content of a  context

```bash
$ apiflows context get --help

Usage: get [options]

get a context description

Options:
  --flowId [flowId]        flow ID
  --contextId <contextId>  context ID
  -h, --help               output usage information
```
* **flowId** is mandatory and define the flowId to which context(s) belongs to
* **contextId** is mandatory.

### How to modify context(s)

```bash
$ apiflows context modify --help
Usage: modify [options]

modify contexts

Options:
  --flowId [flowId]        flow ID
  --contextId [contextId]  context ID
  --groupId [groupId]      group ID
  --file <path>            json file containing description of context
  -h, --help               output usage information
```

* **flowId** is mandatory and define  the **flowId** to which context(s) belongs to
* if **groupId** is defined, all contexts belonging to the group will be modified. 
* if **contextId** is defined, only one context is modified

* **json file** contains a description of the content value, to be applied to context(s). Here is a description of contexts json object : [Context](Context.md). 

### How to delete context(s)

```bash
$ apiflows context delete --help
Usage: delete [options]

delete contexts

Options:
  --flowId [flowId]        flow ID
  --contextId [contextId]  context ID
  --groupId [groupId]      group ID
  -h, --help               output usage information
  ```
* **flowId** is mandatory and define  the **flowId** to which context(s) belongs to
* if **groupId** is defined, all contexts belonging to the group will be deleted. 
* if **contextId** is defined, only one context is deleted

### How to start context(s)


```bash
$ apiflows context start --help

Usage: start [options]

start contexts

Options:
  --flowId [flowId]        flow ID
  --contextId [contextId]  context ID
  --groupId [groupId]      group ID
  --wireIn <wireIn>        wire-in element in which context must be started
  -h, --help               output usage information
  ```
  * **flowId** is mandatory and define  the **flowId** to which context(s) belongs to
* if **groupId** is defined, all contexts belonging to the group will be injected in ApiFlows messaging network. 
* if **contextId** is defined, only one context is injected.
* Injected contexts must be addressed to a **wire-in** 
  node, using its **pin_name** address. Option **--wireIn** is mandatory and must target the **pin_name** of one **wire-in** node of the flow.

  ### How to stop context(s)


```bash
$ apiflows context stop --help

Usage: stop [options]

stop contexts

Options:
  --flowId [flowId]        flow ID
  --contextId [contextId]  context ID
  --groupId [groupId]      group ID
  -h, --help               output usage information

  ```
  * **flowId** is mandatory and define  the **flowId** to which context(s) belongs to
* if **groupId** is defined, all contexts belonging to the group will be modified. Their 'state' property become **STOPPED**. 
* if **contextId** is defined, only one context is modified.Its state' property become **STOPPED**.

Changing **state** property of a context, can have the following effect :
Each time a wire-in node, receives a context message, in **STOPPED** state, it sends the message to its **inactive output**. Depending on how the flow is programmed, sending 

[Back to References](../References.md) | [TOC](../README.md)