# Currying

[Currying](https://en.wikipedia.org/wiki/Currying) is the technique of translating the evaluation of a multi-argument function into evaluating a sequence of single-argument function. Most purely functional programming languages (e.g. [Haskell](https://www.haskell.org/)) do that by default. 

It is also possible to implement curried functions in PowerShell, thanks to the ability of taking `ScriptBlock` as argument and return value. Consider the following PowerShell code to implement a curried a + b function:

```powershell
function Add {
    param([int] $a)
    return {
        param([int] $b)      
        return $a + $b
    }
}
```

Seems like we could easily build a function that takes an arbitary integer and add it with `2`:

```powershell
$addTwo = Add 2
```

Let us try it out with `3`, and the expected value should be `5`:

```powershell
> &$addTwo 3
3
```

Surprisingly, it returns `3` instead of `5`.

This behaviour is caused by the variable scope design of PowerShell. In our `Add` function, `$a` is in **local scope**. `$addTwo` is a `ScriptBlock`, so it does not remember `$a` at all... When we were evaluating `$addTwo`, the value of `$a` was actually `$null`, and in non-strict mode it evaluated to `0`, causing the result to be `3` instead of `5`.

Two make it work, we need to return a [closure](https://en.wikipedia.org/wiki/Closure_\(computer_programming\)), so the enviromental context could be captured:

```powershell
function Add {
    param([int] $a)
    return {
        param([int] $b)      
        return $a + $b
    }.GetNewClosure()
}

> &(Add 2) 3
5
```

> Repro env: Windows 11 22H2, PowerShell Core 7.3.0

## References
- [Get closure with GetNewClosure](https://devblogs.microsoft.com/powershell/get-closure-with-getnewclosure/)

