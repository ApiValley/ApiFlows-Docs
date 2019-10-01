# Flow json object

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**mode** | **String** | sdk or production | 
**replicas** | **Number** | must be set in production mode if autoscale is false | [optional] 
**minReplicas** | **Number** | must be set in production mode  if atoscale is true  | [optional]
**maxReplicas** | **Number** | must be set in production mode  if atoscale is true | [optional]
**autoscale** | **Boolean** | must be set in production. true if ApiFlows must adapt replicas number, based on workload | [optional]


[Back to Cli Reference](ReferenceCli.md) | [Back to Rest API reference](ReferenceRestApi.md)


