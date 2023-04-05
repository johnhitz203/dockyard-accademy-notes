# GenServer

## Purpose 
* Mechanism to hold and update state
  1. Receives a message
  2. Updates state
  3. Sends a return message with the updated state
* GenServer Work Flow
  * Genserver Server
    * Callback functions
      * Client makes a call to GenServer.[call | cast | init]
        * init - Initializes the servers state
        * call - executes handle_call Callback
        * cast - executes handle_cast Callback
  * GenServer Client
    * start_link - Required function
      * Takes the initial state and options
    * GenServer.call - Is an synchronous operation
      * Carries the risk of creating a bottle neck
        * See `/Desktop/DockYardNotesImage/BottleNeckExample.png`
      * timeout - time in milliseconds the caller will exit
        * default: 5000 milliseconds
        * takes non-negative integer | :infinity
  
  ```elixir
  call(server, request, timeout \\ 5000)
  ```
    * GenServer.cast - Is an asynchronous operation
      * Always returns `:ok`
## Use Cases
* Hold state
* LiveView
* OTP - Provide tools to supervise/manage processes

## [[Tags]]