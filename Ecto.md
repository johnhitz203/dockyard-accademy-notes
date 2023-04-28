# Ecto

## Reset Test DB
`$ MIX_ENV=test mix ecto.drop`

## Ecto Query Composition
- While simple queries can be in the context module, complex queries should be handled in a query builder modules in the application core 
  - constructor function - provides a common way to build the foundation for all queries for the specific context
    ```elixir
      def base do
        Demographic # ContextName
      end
    ```
  - reducer function - function that takes some type along with additional arguments, and apply them to return the same type (<ins>This pattern allows queries to be composed</ins>)
    ```elixir
    def for_user(query \\ base(), user) do
      query
      |> where([d], d.user_id == ^user.id)
    end
    ```
  - Add to Context - the query can now be added to the context...
    ```elixir
    def get_demographic_by_user(user) do
      Demographic.Query.for_user(user)
      |> Repo.one()
    end
    ```
    ### Further examples
    ```elixir
    defmodule Pento.Catalog.Product.Query do
      import Ecto.Query
      alias Pento.Catalog.Product
      alias Pento.Survey.Rating

      def base, do: Product

      def with_user_ratings(user) do
        base()
        |> preload_user_ratings(user)
      end

      def preload_user_ratings(query, user) do
        ratings_query = Rating.Query.preload_user(user)
        query
        |> preload(ratings: ^ratings_query)
      end
    end
    ```
    ```elixir
    defmodule Pento.Catalog.Product.Query do

    def base, do: Product
    def with_user_ratings(user) do
      base()
      |> preload_user_ratings(user)
    end
    def preload_user_ratings(query, user) do
      ratings_query = Rating.Query.preload_user(user)
      query
      |> preload(ratings: ^ratings_query)
    end
    ```
    Examples from Programming LiveView (pg 160-161): interactive Elixir web programming without writing any JavaScript
        (Tate & DeBenedetto - The Pragmatic Bookshelf - 2022)