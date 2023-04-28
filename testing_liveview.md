# Testing LiveView

## Test that it mounts
* use async: true for most cases
* need to import Phoenix.LiveViewTest
  * can import in each test module
  * can add the import to the conn_case.ex in test support
* testing pre-connected and connected mounts
  * may have different behavior pre-connected v connected
  ```elixir
  socket = if connected?(socket) do
    assign(socket, count: 5
  else
    assign(socket, count: 0)
  end  
  ```

## Test what happens when you send messages
* 