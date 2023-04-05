# Double Ended Queues

## Vocabulary
* ADT - Abstract Data Type
  * A way to organize AND act upon data
* Abstraction - A shared definition that serves a common purpose
  * Concepts - Should not be to strongly held
* Queue - A list of data items stored so as to be retrievable in a definite order, usually the order of insertion
  * Amortized Queue - 
    * Usually O(1)
    * Sometimes O(n) - When we need to reverse a chunk of data
  * concepts
    * Front v Back
    * Start v End
    * Entry v Exit
    * Arrive v Depart
* Big O Notation - Represents the time complexity of an operation
  * O(1) - Constant for O(n) where n is the number of elements
  * O(n) - Time expands as the number of elements increases

## Thinking Process
* What assumptions are we bring to our problem space
  * How do you remove your prior experience from the thought process
* We need to think about our problems abstractly
  * Play with abstractions before trying to implement a solution

## Data Type v Abstract Data Type
* List vs Queue
* Map vs Double Ended Queue
* Tuple vs Tree
* Keyword List vs Module/Struct 
* Class/Object

## Code
### First implementation
* Order of implementation matters
```elixir
defmodule FirstInLastOut do

def new() do
  []
end

#back #last #newest > Front to the q is the end of the list
def arrive(q, element) do 
  [element | q]
end

def depart(q) do #front #next #oldest
  [head | tail]
  tail
end
```

## Second Implementation
```elixir
defmodule FirstInLastOut do

def new() do
  []
end

def arrive(q, element) do #back #last #newest
  [element | q]
end

def depart(q) do #front #next #oldest
  {hd(Enum.reverse(q)), tl(Enum.reverse(q))}
end
```

## Brooks Implementation
```elixir
defmodule AmortizedQueue do
  def new() do
    back = []
    front []
    {back, front}
  end

  def arrive({back, front}, el) do
    new_back = [el | back]
    {new_back, front}
  end

  def depart({back, []}) do
    [head | tail] = Enum.reverse(back)
    {head, {[],tail}}
  end

  def depart({back, [head | new_front]}) do
     # removed (element), new_front
     {head, {back, new_front}}
  end
end
```





