# Priority Queue w/ Binary Search Tree

## Tree
- has a node with child nodes
- has two constraints
  - no cycles - child can not refer back to parents
  - nodes do not have multiple parents (graph is a data structure with multiple parents)
- has not constraints w/ regard to position (ie does not have order)

## Binary Search Tree
- a tree with ordered data
  - all data on left is less than
  - all data on right is greater than
- efficient search because at any point in the BST you can rule out half of the data

```elixir
def module BST do
  def new() do
   {}
  end

  def new(priority, data) do
    {new(), {priority, data}, new()}
  end

  def empty?(tree) do
    tree == new()
  end

  def insert(tree, priority, data) do
    # inserted element never becomes a parent. That is it
    # is always inserted as an empty sub-tree.
    empty = new()
    case tree do
      # ~~new() -> new(priority, data)~~ not allowed
      ^empty -> new(priority, data) || {} -> new(priority, data)
      {left, {p, d}, right} ->
        if priority > p do
          {left, {p, d}, insert(right, priority, data)}
        else
          {insert(left, {p, d}, right)}
        end
    end
  end

  def find_min(tree) do
  end

  def remove_min(tree) do
  end
end
```