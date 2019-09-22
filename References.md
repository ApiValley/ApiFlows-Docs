# ApiFlows References

[TOC](./README.md#table-of-content) | [NEXT GUIDE](./Tutorial.md)


* [ApiFlows CLI](#apiflows-cli)
* [ApiFlows REST Api](#apiflows-rest-api)
* [ApiFlows NodeRED nodes](#apiflows-nodered-nodes)
* [ApiFlows metrics](#apiflows-metrics)

## ApiFlows CLI

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

user, account, subscription subcommand are not yet available in ApiFlows MVP2.
As a consequence, only flow and context subcommand are documented in the following

### flow subcommand

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

#### how to 


[Back to top](#apiflows-references)

## ApiFlows REST Api

### flow REST API

Method | HTTP request | Description
------------- | ------------- | -------------
[**createFlows**](#createFlows) | **POST** /v1/flows | Create a new flow
[**deleteFlow**](#deleteFlow) | **DELETE** /v1/flows/{flowid} | Delete a flow
[**getFlowId**](#getFlowId) | **GET** /v1/flows/{flowid} | Returns flow information
[**getFlows**](#getFlows) | **GET** /v1/flows | Returns flows inventories 
[**patchFlow**](#patchFlow) | **PATCH** /v1/flows/{flowid} | Patch a flow
[**putFlow**](#putFlow) | **PUT** /v1/flows/{flowid} | Update a flow


<a name="createFlows"></a>
## **createFlows**

Create a new flow





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**Flow**](Flow.md)| Flow object that needs to be added | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="deleteFlow"></a>
## **deleteFlow**

Delete a flow





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow to delete | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="getFlowId"></a>
## **getFlowId**

Returns flow information

Returns the description of a flow for an account



### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow to return | 

### Return type

[**FlowStatus**](FlowStatus.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getFlows"></a>
## **getFlows**

Returns flows inventories 

Returns the list of ongoing flows for an account



### Parameters
This endpoint does not need any parameter.

### Return type

[**[FlowStatus]**](FlowStatus.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="patchFlow"></a>
## **patchFlow**

Patch a flow





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow to patch | 
 **body** | [**Flow**](Flow.md)| Flow object that needs to be patched | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="putFlow"></a>
## **putFlow**

Update a flow




### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow to update | 
 **body** | [**Flow**](Flow.md)| Flow object that needs to be updated | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

[Back to top ApiFlows REST Api](#apiflows-rest-api)

[Back to top](#apiflows-references)

### Contexts REST Api

All URIs are relative to *https://apiflows-rest.apivalley.org/api*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createContexts**](#createContexts) | **POST** /v1/flows/{flowid}/contexts | Create new contexts for a flow
[**deleteContextId**](#deleteContextId) | **DELETE** /v1/flows/{flowid}/contexts/{contextId} | Delete one context
[**deleteContexts**](#deleteContexts) | **DELETE** /v1/flows/{flowid}/contexts | delete a group of contexts for a flow
[**getContextId**](#getContextId) | **GET** /v1/flows/{flowid}/contexts/{contextId} | get one context
[**getContexts**](#getContexts) | **GET** /v1/flows/{flowid}/contexts | Returns the list of ongoing contexts for a flow
[**modifyContextId**](#modifyContextId) | **PUT** /v1/flows/{flowid}/contexts/{contextId} | update one context data
[**modifyContexts**](#modifyContexts) | **PUT** /v1/flows/{flowid}/contexts | modify data of a group of contexts for a flow
[**operateContextId**](#operateContextId) | **PATCH** /v1/flows/{flowid}/contexts/{contextId} | start or stop one context
[**operateContexts**](#operateContexts) | **PATCH** /v1/flows/{flowid}/contexts | start or stop a group of contexts for a flow


<a name="createContexts"></a>
## **createContexts**

Create new contexts for a flow





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **body** | [**Context**](Context.md)| Context object that needs to be updated | 
 **nb** | **Number**| number of context objects to create | 
 **groupId** | **String**| context group id. Created context Id will start with group id | [optional] 
 **operation** | **String**| start inject the context in a specific wire-in. stop eject the context from any wire-in | [optional] 
 **wireIn** | **String**| wire-in Id, where context must be injected | [optional] 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="deleteContextId"></a>
## **deleteContextId**

Delete one context





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **contextId** | **Number**| ID of context to delete | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="deleteContexts"></a>
## **deleteContexts**

delete a group of contexts for a flow





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **groupId** | **String**| Group id. Only contexts for which id starts with group id, will be deleted | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="getContextId"></a>
## **getContextId**


get one context



### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **contextId** | **Number**| ID of context to return | 

### Return type

[**ContextStatus**](ContextStatus.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="getContexts"></a>
## **getContexts**

Returns the list of ongoing contexts for a flow



### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **groupId** | **String**| context group id. Only context Id starting with group Id will be listed | [optional] 

### Return type

[**[ContextStatus]**](ContextStatus.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

<a name="modifyContextId"></a>
## **modifyContextId**

update one context data





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **contextId** | **Number**| ID of context to update | 
 **body** | [**Context**](Context.md)| Context object that needs to be updated | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="modifyContexts"></a>
## **modifyContexts**

modify data of a group of contexts for a flow




### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **groupId** | **String**| Group id. Only contexts for which id starts with group id, will be patched | 
 **body** | [**Context**](Context.md)| Context object that needs to be updated | 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="operateContextId"></a>
## **operateContextId**

start or stop one context





### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **contextId** | **Number**| ID of context to patch | 
 **operation** | **String**| start inject the context in a specific wire-in. stop eject the context from any wire-in | [optional] 
 **wireIn** | **String**| wire-in Id, where context must be injected. mandatory if operation is start | [optional] 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json

<a name="operateContexts"></a>
## **operateContexts**

start or stop a group of contexts for a flow


### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **flowid** | **Number**| ID of flow which created the contexts | 
 **groupId** | **String**| Group id. Only contexts for which id starts with group id, will be patched | 
 **operation** | **String**| start inject the context in a specific wire-in. stop eject the context from any wire-in | 
 **wireIn** | **String**| wire-in Id, where context must be injected. Mandatory if operation is start | [optional] 

### Return type

[**ApiResponse**](ApiResponse.md)

### Authorization

[af_auth](../README.md#af_auth)

### HTTP request headers

 - **Content-Type**: application/json, application/xml
 - **Accept**: application/xml, application/json


## ApiFlows NodeRED nodes

### **ApiFlows context node**
This node is used to read, update, or delete a shared context from a NodeRED flow.
It appears in palette in category **ApiFlows**  under the name **ApiFlows context**.

One input message :
* must contain **af_contextid** field for any operation
* must contain **af_context** field for **SET** operation
* must contain **af_state** field for **TOSTATE** operation

Two output messages : **error** and **result**
* error output message is sent in case of context processing error. It has the same content  as input message except **error** field which contains the error which occured during context processing
* result output message is sent in case of context processing success. It has the same content as input message except **af_context** which potentially changed during a **GET** operation.

Two parameters :

* name : label of node as it appears in the flow
* operation : can be GET, SET, DELETE, TOSTATE

Four operations :

**GET** is used to read the context with af_contextid ID. The read result is put into **af_context** field of result output.

**SET** is used to update the content of the context with **af_contextid** ID. New context value is taken from **af_context** input message field.

**DELETE** is used to delete the content of the context with **af_contextid** ID.

**TOSTATE** is ued to change the **state** of context with **af_contextid** ID. New state value is taken from **af_state** input message field.

### **ApiFlows wire-in node**

one input  :

* must contain **af_contextid** field
* may contain **af_wirein** if it's at least the second time, message go through a wire-in node. Value of the field is the **pin_name** of last crossed wire-in node.

Three outputs :
* **active** output message is sent if input message contains **af_contextid** field, and context data for this context ID is not empty, and context state for this context ID is **NOT STOPPED**. It has the same context as input message except **af_context** and **af_state** which respectively contain context data and context state values for **af_contextid** ID. **af_wirein** field contains the **pin_name** value. It's a marker to let ApiFlows knows the message went through the wire-in node.

* **inactive** output message is sent if input message contains **af_contextid** field, and context data for this context ID is not empty, and context state for this context ID is **STOPPED**. It has the same context as input message except **af_context** and **af_state** which respectively contain context data and context state values for **af_contextid** ID.**af_wirein** field is removed.

* **error** output message is sent if input message does not contain **af_contextid** field, or context data for this context ID is empty, or error occured during read operation for this context ID. It has the same context as input message excep **error** field which contains the error which occured during read context operation of **af_contextid** ID. **af_wirein** field is removed.

Two parameters :

* **name** : label of node as it appears in the flow
* **pin_name** : address of the wire-in input node in ApiFlows messaging network.


### **ApiFlows wire-out node**

### **ApiFlows metric node**



[Back to top](#apiflows-references)

## ApiFlows metrics

[Back to top](#apiflows-references)




[TOC](./README.md#table-of-content) | [NEXT GUIDE](./Tutorial.md)