```elixir
defmodule Year do
  @moduledoc """
  This module contains the leap_year? function
  """

  @doc """
  Returns whether 'year' is a leap year.

  A leap year occurs:

  on every year that is evenly divisible by 4
    except every year that is evenly divisible by 100
      unless the year is also evenly divisible by 400
  """
  @spec leap_year?(non_neg_integer) :: boolean
  def leap_year?(year) do
    cond do
      rem(year, 400) == 0 -> true
      rem(year, 100) == 0 -> false
      rem(year, 4) == 0 -> true
      true -> false
    end
	# or using case
    case {rem(year, 400), rem(year, 100), rem(year, 4)} do
      {0, _, _} -> true
      {_, 0, _} -> false
      {_, _, 0} -> true
      _ -> false
    end
  end
end
```

# Cond
**Explanation:**

- **`rem(year, 400) == 0`**:  
    If the year is divisible by **400**, it's a leap year — this condition takes **highest priority**.
    
- **`rem(year, 100) == 0`**:  
    If it _wasn't_ divisible by 400 but **is divisible by 100**, it's _not_ a leap year.
    
- **`rem(year, 4) == 0`**:  
    If the year isn't divisible by 400 or 100, but **is divisible by 4**, it's a leap year.
    
- **`true -> false`**:  
    This is the **fallback** — the year is not divisible by 400, 100, or 4, so it's not a leap year.
# Case
### ✅ Why this works logically

- The first match rules out 400-divisible years.
    
- The second match handles 100-divisible years that aren't 400.
    
- The third match can assume year is:
    
    - Not divisible by 400 (otherwise would’ve hit the first case),
        
    - Not divisible by 100 (otherwise would’ve hit the second case),
        
    - But divisible by 4 → leap year.
        
- The `_` fallback then catches non-leap years.

## 🔬 Comparison MFCs vs `cond` and `case`

| Feature                    | `MFC with guards`                                     | `cond`                             | `case`                             |
| -------------------------- | ----------------------------------------------------- | ---------------------------------- | ---------------------------------- |
| **Performance**            | 🔥 Fastest – short-circuits and avoids tuple creation | ⚡ Fast – short-circuits, no tuples | 🐢 Slower – evaluates all 3 `rem`s |
| **Short-circuit behavior** | ✅ Yes                                                 | ✅ Yes                              | ❌ No – all computed up front       |
| **Clarity**                | ✅ Very clear, declarative                             | ✅ Clear and readable               | 😐 Less obvious to beginners       |
| **Idiomatic Elixir**       | ✅ Extremely idiomatic                                 | ✅ Also idiomatic                   | ⚠️ Less idiomatic for this case    |
| **Compiled form**          | Efficient native pattern match dispatch               | Nested ifs                         | Tuple + match logic                |

## 🔍 What's the key difference?

### 1. `cond`:

elixir

CopyEdit

`def leap_year?(year) do   cond do     rem(year, 400) == 0 -> true     rem(year, 100) == 0 -> false     rem(year, 4) == 0 -> true     true -> false   end end`

- Elixir compiles this into a **single function** body with a **chain of conditional branches** (essentially `if/else`).
    
- At runtime, **each `rem/2` call is evaluated one-by-one**, **in order**, unless an earlier condition short-circuits.
    

---

### 2. MFC with Guards:

elixir

CopyEdit

`def leap_year?(year) when rem(year, 400) == 0, do: true def leap_year?(year) when rem(year, 100) == 0, do: false def leap_year?(year) when rem(year, 4) == 0, do: true def leap_year?(_), do: false`

- This defines **separate function clauses**, and Elixir compiles them into **pattern-matching clauses** in the compiled BEAM bytecode.
    
- When you call `leap_year?/1`, the BEAM uses a **dispatch table** to quickly find the first clause whose guard passes — no need to evaluate all the conditions manually like in `cond`.
    
- **If the first guard matches, it jumps straight there.**
    

---

## 🧠 Why it's faster

| Feature                  | `cond`                                  | MFC with guards                     |
| ------------------------ | --------------------------------------- | ----------------------------------- |
| Structure                | One function body with nested checks    | Multiple compiled clauses           |
| Evaluation strategy      | Sequential checking                     | Guard-based dispatch                |
| `rem/2` calls at runtime | Always evaluated in order (up to match) | Stops at the first matching clause  |
| BEAM optimization        | Less                                    | ✅ Pattern matching + guard dispatch |