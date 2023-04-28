# State with Agents and ETS

## ETS 
* in memory key/value data store
* linier time 

## Scaling
  * spin up more processes
    * can overload memory
    * cost
    * can be addressed with worker pools
      * poolboy - library
      * registry - method of organizing processes
  * use rate limiting
    * queuing
  * priority queue
  * Shedding load

## Rate Limiting Requests

## Parallelism v Concurrency
* Concurrency - switching between tasks
* Parallelism - doing multiple tasks at the same time