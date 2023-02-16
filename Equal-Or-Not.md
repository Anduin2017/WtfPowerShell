# Equal Or Not?

## Null or not null

When you have something which is null:

```powershell
$something = $null
```

And test it with eq:

```powershell
$something -eq $null
```

Which outputs:

```
True
```

But when you have something string which is null:

```powershell
[string]$something = $null
```

And test it with eq:

```powershell
$something -eq $null
```

Which outputs:

```
False
```

The underlying fact is, in PowerShell, **`-eq` operator does NOT satisfy the commutative law**. Which means, the result of `$a -eq $b` does not always equal to `$b -eq $a` if `$a` and `$b` have different types.

Variables in PowerShell could be divided into two types:

- **Scalar**: if the variable only contains a single value (e.g. a `string`)
- **Collection**: if the variable contains multiple values (e.g. an array of `string`)

And the return value of `-eq` is different based on the type of the left-hand value. If the left-hand value and the right-hand value have different type of data type (scalar or collection), the right-hand value will be casted to match the type of the left-hand value.

- Returns `Boolean` if the left-hand side is a scalar, determined by whether the left-hand side and the right-hand side are the exact match.
- Returns any matching values if the left-hand side is a collection. If nothing got matched, an empty array is returned.

In above case, on the left-hand side, when `$null` is force converted to `string`, it becomes an empty string (which is a scalar). The right-hand value `$null` is also a scalar, so no typecasting is needed. An empty string is not `null`, so the return value should be `False`.

## ...and the fun begins

Let's start by comparing an `Int` to a collection of `Int`:

```powershell
1 -eq @(1)
```

What should the result be?

It should be `False`. `1` is a scalar but `@(1)` is not. `@(1)` need to be casted to `Int` for comparasion, which is unsupported in PowerShell.

But what if we compare a string to a collection containg the exact same string?

```powershell
"test" -eq @("test")
```

Guess what? It returns `True`.

The difference here is that `@("test")` could be casted to `String`, which result in `"test"`. So the left-hand value and the right-hand value are both `[string]"test"` during comparasion.

This also explains why:

```powershell
"1 234" -eq @("1", "234")
```

would yield `True` as its result.

What a strange behavior of PowerShell! 😲

## Lessons learnt

Never assume `-eq` operator to satisfy the commutative law. When doing null checks, always put `$null` on the left-hand side.

## References

- [about Comparison Operators - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_comparison_operators)
- [PossibleIncorrectComparisonWithNull - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/utility-modules/psscriptanalyzer/rules/possibleincorrectcomparisonwithnull)

> Repro env: Windows 11 22H2, PowerShell Core 7.3.2
