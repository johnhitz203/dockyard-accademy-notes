# control_flow

Dictates when and why things are done

###
* if/else - One or two paths where a thing is true
  * Evaluates truthiness of the value
* case - Multiple patterns match the case
  * A safer option that if/else - Will fail if the data is not what we expect
  * More readable than if(?)
  * More extensible than if
* cond - When there are multiple conditions that are true
* guards -
* pattern matching 
* booleans
* Enum + comprehension
  ```elixir
  [1, 2, 3] |> Enum.filter(&is_integer/1)
  ```
* with
* polymorphism
  * protocol - data based
  * behavior - polymorphism based on a common interface (ie )
    * mocks - define a specific behavior that creates an extendable pattern 
    * GenServer - 