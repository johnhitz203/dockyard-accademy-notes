# Tags (Book Search: Tags Reading)

## Many-TO-Many -
* A bidirectional relationship where two records have many fields in common
  * Creates a join table
  `~/Desktop/DockYardNotesImage/ManyToManyMigration.png`
  * Need to set up many-to-many relationship in both schema and migration
    * 
    1. many_to_many macro on item to be tagged
       1. put_assoc on item to be tagged - puts the tag_id into the book struct
       2. cast_assoc on tag - Used for external data that needs to be validated before assertion
    2. Create Context
```elixir
def create_book(attr \\ %{}, )
```

```elixir
<%= multipl_select f, :tags, [{"label", "value"}] %>
```
    3. Pass data from controller or view
  
### Join Through Table
1. Create the table w/ mix phx.gen.html Tags Tag tags name:string
   1. Create update tag migration
   2. Create migration for mix `ecto.gen.migration posts_tags_join`
      1. Add references for posts and tags
         1. ```elixir
            def change do
              create table (post_tags) do
                add(:post_id, references(:posts, on_delete: :delete_all), null: false)
                add(:tag_id, references(:tags, references(:tags, on_delete: :delete_all), null: false)))
            end

            create(unique_index(:post_tags, [:post_id, :tag_id]))
            ```
2. Create