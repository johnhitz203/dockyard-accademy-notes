# task_review
## Use Case
* Allows code to be executed in an independent process that is OTP-compliant
  * Can be supervised
  * Improved error handling
  
## Task Functions
* Task.start/1 - Creates a new fire-and-forget process
  * Non-blocking - Task process does not block the caller
  * Does not return
* Task.async/1 - Spawn a process that performs some calculation that returns a value
* Task.await/1 - Used to receive a value from a process that is spawned with Task.async/1
