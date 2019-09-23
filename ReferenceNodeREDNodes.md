# ApiFlows NodeRED nodes

[Back to References](References.md) | [TOC](README.md)

## **ApiFlows context node**
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

**TOSTATE** is used to change the **state** of context with **af_contextid** ID. New state value is taken from **af_state** input message field.

## **ApiFlows wire-in node**

one input  :

* must contain **af_contextid** field
* may contain **af_wirein** if it's at least the second time, message go through a wire-in node. Value of the field is the **pin_name** of last crossed wire-in node.

Three outputs :
* **active** output message is sent if input message contains **af_contextid** field, and context data for this context ID is not empty, and context state for this context ID is **NOT STOPPED**. It has the same context as input message except **af_context** and **af_state** which respectively contain context data and context state values for **af_contextid** ID. **af_wirein** field contains the **pin_name** value. It's a marker to let ApiFlows knows the message went through the wire-in node.

* **inactive** output message is sent if input message contains **af_contextid** field, and context data for this context ID is not empty, and context state for this context ID is **STOPPED**. It has the same context as input message except **af_context** and **af_state** which respectively contain context data and context state values for **af_contextid** ID.**af_wirein** field is removed.

* **error** output message is sent if input message does not contain **af_contextid** field, or context data for this context ID is empty, or error occured during read operation for this context ID. It has the same context as input message except **error** field which contains the error which occured during read context operation of **af_contextid** ID. **af_wirein** field is removed.

Two parameters :

* **name** : label of node as it appears in the flow
* **pin_name** : address of the wire-in input node in ApiFlows messaging network.


## **ApiFlows wire-out node**

one input :

## **ApiFlows metric node**




[Back to References](References.md) | [TOC](README.md)