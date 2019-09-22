# ApiFlows Tasks

[TOC](./README.md#table-of-content) | [NEXT GUIDE](./References.md)


* [Create a flow in sdk mode](#create-a-flow-in-sdk-mode)
* [Modify a flow in sdk mode](#modify-a-flow-in-sdk-mode)
* [Create shared contexts](#create-shared-contexts)
* [Inject shared contexts](#inject-shared-contexts)
* [Modify shared contexts](#modify-shared-contexts)
* [Create and modify grafana dashboard](#creater-and-modify-grafana-dashboard)
* [Switch to production mode](#switch-to-production-mode)

## Create a flow in sdk mode

Prerequisites : [Setup](#./Setup.md)

* prepare a json file /path_to_json_file/myFlow.json with the following content  :

```json
{
      flowId: myFlow
      mode: sdk
}
```

**flowId** is of type string : It's the Id of the flow you want to create 

**mode** is of type string and must be "sdk" to start the flow in sdk mode





* Request the creation of the flow MyFlow
```bash
> apiflows flow create --file /path_to_json_file/myFlow.yaml
```
* Connect to the flow visual editor

Wait for around 1 minute after flow creation request. ApiFlows SaaS created a NodeRED instance for you in the cloud.  You can access its visual editor at the following address : http://


[Back to top](#apiflows-tasks)

## Modify a flow in sdk mode

[Back to top](#apiflows-tasks)

## Create shared contexts

[Back to top](#apiflows-tasks)

## Inject shared contexts

[Back to top](#apiflows-tasks)

## Modify Shared contexts

[Back to top](#apiflows-tasks)

## Create and modify grafana Dashboard

[Back to top](#apiflows-tasks)

## Switch to production mode

[Back to top](#apiflows-tasks)





[TOC](./README.md#table-of-content) | [NEXT GUIDE](./References.md)