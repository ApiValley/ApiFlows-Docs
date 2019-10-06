# ApiFlows Tutorial

[TOC](./README.md#table-of-content) 

* [Node-RED basic service](#node-red-basic-service)
* [Node-RED basic tester](#node-red-basic-tester)

## Node-RED basic service

Node-RED already has many different connectors to implement multiple kind of services. For example, it can act as a web server to provide de service. In the following example, it provides a service to compute the sinus of an angle provided in the http request's parameters:

![Basic NodeRed service](images/NodeRedBasicService.png)

[Basic NodeRed flow](images/NodeRedBasicService.json)

The service can be reached using the NodeRed host name and the path /sinus:
http://<flowId>.<accountId>.apivalley.org/sinus?q=32151.1

## Node-RED basic tester



 [Back to top](#apiflows-concepts)