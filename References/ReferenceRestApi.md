# ApiFlows REST Api
[Back to References](../References.md) | [TOC](../README.md)
## flow REST API

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

## Contexts REST Api

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


 [Back to References](../References.md) | [TOC](../README.md)