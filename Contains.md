# Contains

Consider the following snippet:

```powershell
"12-18" -Contains "-"
```

You’d think this evaluates to true.

But it doesn't. This will evaluate to `false` instead. 

I’m not sure why this happens, but it does.

But if you try:

```powershell
"12-18".Contains("-")
```

Now the expression will evaluate to `$true`.

This is because `-Contains` is an operator on collection, while `.Contains()` refers to `String.Contains` method in .NET which operates on `string`.

And, `string` is not seen as a collection of `char`.

Bonus:

``` powershell
"12-18" -Contains "12-18"
```

Guess what, it evaluates to `true`.

This is because `-Contains` could only be applied to a collection value, so the left-hand value `"12-18"` will to be casted to `string[]`, resulting in `@("12-18")`. From this point on, the behavior makes total sense.

What a strange behavior of PowerShell! 😲

> Repro env: Windows 11 22H2, PowerShell Core 7.3.2