# live_view

## Initial LiveView Request/Response
* Initial mount renders dead view w/ JavaScript 
* Second mount uses the socket established by the initial render (MountFunction4_3_2023.png)
    ```elixir
    def mount(params, session, socket) do
      if connected?(socket) do
        IO.inspect("Connected Mount")
      else
        IO.inspect("Disconnected Mount")
      end

      {:ok, assign(socket, :count, 0)}
    end
    ```
  * Render Function
    ```elixir
    def render(assigns) do
      ~H"""
      Count: <%= @count %>
      <button phx-click="increment">Inc</button>
      """
    ```
    ```elixir
    def handle_event("inc", _params, socket) do
      assign(socket, :count, socket.assigns.count + 1)
      {:noresponse, socket}
    end
    ```
* LiveView Forms
  * phx-submit
  * phx-change - Fired when form changes
    * real time search
    * validation
    * automatic save
   ```elixir
    def render(assigns) do
      ~H"""
      Count: <%= @count %>
      <button phx-click="increment">Inc</button>

      <.form let={f} for={increment_form} phx-submit="inc_submit" phx-change="inc_change">
        <%= number_input f, "inc_by %>
        <%= submit "Submit" %>

      </.form
      """
    ```

    ```elixir
    def handle_event("inc_submit", params, socket) do
       assign(socket, :count, )
      {:noreply, assign(socket, :count, socket.assigns.count + string.to_integer(params.["inc_by]))}
    end
    ```
    * Example Code
      * increment_change.png
      * handling_empty_string.png
  * Controlled Forms

## Injecting Values in HTML
* {} - Used to inject elixir code into Heex templates
* socket.assigns - Map that holds state for the LiveView
* assign - Updates the value of the assigns Map
  * assign/3 - Takes the socket, key, and value `assign(socket, :key, value)
  * assign/2 - Takes the socket and a keyword list `assign(socket, key1: val1, key2: val2, ...)

## LiveView and Ecto


## LiveView Navigation
<ins>Note:</ins> - An updated URL does not necessarily correspond ot a different LiveView

### Navigation
* Four main things - Can reset state or not depending on the navigation function used

### Live vs Push
* Live - Used on the front end (in HTML)
  *  Creates a link in the Heex template
* Push - Used on the server (in .ex files)
  * Creates a function in the .ex files
### Redirect vs Patch
* Redirect - Re-mounts the LiveView
* Patch - Does not Re-mount the LiveView
  
#### Redirect and Patch Functions
* live_redirect - Redirects to a new page and fires the mount function
  * Starts a new process
  * Resets state
* live_patch - Reloads the current LiveView 
  without firing the mount
  * Does not create a new process
  * Updates the URL
  * Does not reset state
* push_redirect - Returns to base URL and remounts the LiveView
* push_patch - Does not remount the LiveView eg it does not retrieve any new data that has been created

## Image Upload(files)
<ins>Note: </ins> State is held in the `socket`

* We need to ready the state for uploads
  ```elixir
  def mount(_params, _session, socket) do
    {:ok, allow_upload(socket, :my_images, accept: ~w(.jpg .jpeg) max_entries: 2)}
  end
  ``` 
  * `~w(...)` - can be any file type
    * `~w` - converts to a list of strings
  * The above code creates an @uploads key on the socket.
  * `<.live_file_input @uploads.media>`
    * `<%= live_file_input @uploads.media>` in LiveView 0.17

### Three Steps
1. Prime socket with key and file type with allow_upload
2. Add live_file_input to form html
3. Consume the image - Move it from the tmp directory to the "priv/static/image/file_name"
   `consume_uploaded_entries`
4. Display the image

## Preview Images
* `@uploads.media.entries` - Where `midia` is the key in mount
* Users file name - Stored in `entries.client_name`

## Drag-And-Drop
```html
<label id="drag-n-drop"  class="drag-n-drop" phx-drop-target={@uploads.picture.ref}>
      Click or drag and drop to upload image
      <%= live_file_input @uploads.picture, style: "display: none;" %>
</label>
```
