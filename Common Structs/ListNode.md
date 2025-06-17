The following is the ListNode structure which functions as a linked list implemented via the map type.
```elixir
defmodule ListNode do
  @type t :: %__MODULE__{
          val: integer(),
          next: ListNode.t() | nil
        }
  defstruct val: 0, next: nil
end
```
# Functions
Given below are interconversion functions between the custom linked list type and the native one:
```elixir
  def ll_to_ln(ll, acc \\ nil)

  def ll_to_ln([], acc), do: acc

  def ll_to_ln([head | tail], acc) do
    acc = %ListNode{val: head, next: acc}
    ll_to_ln(tail, acc)
  end

  def ln_to_ll(ln, acc \\ [])

  def ln_to_ll(nil, acc), do: acc

  def ln_to_ll(%ListNode{val: head, next: tail}, acc) do
    acc = [head | acc]
    ln_to_ll(tail, acc)
  end
```
Both functions give the reversed result and would need to be manually reverse to provide the actual result.