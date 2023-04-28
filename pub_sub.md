# pub_sub

## What Is PubSub
* Allows a process to broadcast messages to all subscribed processes
  * Publisher - Process that sends a message to the pubsub system which sends a message to all subscribers
  * Subscriber - Receives messages from the PubSub system
  * Topic - Identifies messages being sent so they can be directed to the correct subscribers
  * payload - data sent with message

## Create
* Subscribe to message in mount
* Broadcast on new message handler
  * broadcast() - Sends a message to the whole cluster
  ```elixir
  ```
  * broadcast_from() - Does not send a message to itself
    ```elixir
    ```

* handle_info for message
  * We can filter the message list in handle_info or in the handle_event for the action
  ```elixir
  def handle_info(%{topic: "broadcast_message"}, socket) do
    {:noreply, assign(socket, :boadcast_message, list_message())}
  end
  ```

## Delete
  ```elixir
  def handle_info(%{topic: "delete_message}) do
    {:noreply, assign(socket, :delete_message, socket)}
  end