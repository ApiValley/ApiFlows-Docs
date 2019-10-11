# **ApiFlows metrics**

[Back to References](../References.md) | [TOC](../README.md)

## System metrics

* kubernetes_deployment_status_replicas_available
 
    * gauge 
    ```
    GOAL : Get the number  Node-RED instances executing a ApiFlows flow.

    INFLUXQL: SELECT sum("gauge") FROM "kubernetes_deployment_status_replicas_available" WHERE  ("deployment" =~ /^nodered-.*-$flowId/) AND $timeFilter GROUP BY time($__interval) fill(previous)
    ```
* kubernetes_pod_container
    * cpu_usage_nanocores
    ```
    GOAL : Get the total number of vCores used by the Node-RED  instances executing a ApiFlows flow.
    
    INFLUXQL: SELECT sum("cpu_usage_nanocores")/1000000000 FROM "kubernetes_pod_container" WHERE ("pod_name" =~ /^nodered-.*-$flowId.*$/) AND $timeFilter GROUP BY time($__interval) fill(previous)
    ```
    * memory_usage_bytes
    * memory_rss_bytes
    * memory_page_faults
* kubernetes_pod_network
    * rx_bytes
    ```
    GOAL: Get the total number of kB/s  received by Node-RED instances executing a ApiFlows  flow

    INFLUXQL:  
    ```
    * rx_errors
    
    * tx_bytes
    ```
    GOAL: Get the total number of kB/s  sent by Node-RED instances executing a ApiFlows  flow

    INFLUXQL:  
    ```
    * tx_errors
    ```
    GOAL: Get the total number of kB/s  received by Node-RED instances executing a ApiFlows  flow

    INFLUXQL:  
    ```
* af_node_red_gauge_af_event_nodered_loop_nb
* af_node_red_gauge_af_event_nodered_loop_lag


## User defined metrics. Defined with ApiFlows metric node-RED node

* af_node_red_\<metric-type\>\_metric\_\<metric-name\>
    * \<metric-type\>

### Example :

* af_node_red_counter_metric_sinuscomputed
    * counter
    ```
    GOAL1 : Get the number of computed sinus since the deployment of sinus service

    INFLUXQL1 :  SELECT max("sum") from (SELECT sum("counter") as "sum" FROM "af_node_red_counter_metric_sinuscomputed" WHERE ("flowId" = '$flowId' ) AND $timeFilter GROUP BY time($__interval) fill(previous)) WHERE $timeFilter GROUP BY time(1m) fill(previous)

    GOAL2 : Get the number of computed sinus per second

    INFLUXQL2: select non_negative_derivative("max",1s) from (SELECT max("sum") as "max"  from (SELECT sum("counter") as "sum" FROM "af_node_red_counter_metric_sinuscomputed" WHERE ("flowId" = '$flowId' ) AND $timeFilter GROUP BY time($__interval) fill(previous)) WHERE $timeFilter GROUP BY time(1m) fill(previous)) where $timeFilter fill(previous)
    ```



## ApiFlows node-red nodes metrics

* af_node_red_counter_context_set_success
* af_node_red_counter_context_set_error
* af_node_red_counter_context_get_success
* af_node_red_counter_context_get_error
* af_node_red_counter_context_delete_success
* af_node_red_counter_context_delete_error
* af_node_red_counter_context_tostate_success
* af_node_red_counter_context_tostate_error
* af_node_red_counter_context_input_error
* af_node_red_counter_context_connexion_error
* af_node_red_counter_wire_in_success
* af_node_red_counter_wire_in_error
* af_node_red_counter_wire_out

## 

[Back to References](../References.md) | [TOC](../README.md)