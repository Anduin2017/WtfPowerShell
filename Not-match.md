# Not match is different than notmatch?

## Obviously

```powershell
-not $false
```

Which outputs `True`.

And:

```powershell
-not $true
```

Which outputs `False`.

## And obviously

```powershell
"aabaa" -match "b"
# True
```

And of course:

```powershell
-not "aabaa" -match "b"
# False
```

Em. I like it.

So I kept developing... And...

```powershell
"aaaa" -match "c"
```

Which is `False`.

But:

```powershell
-not "aaaa" -match "c"
```

Which is also `False`!?

So `-not False` is `False`?

What a strange behavior of PowerShell! 😲

> Repro env: Windows 11, PowerShell Core 7.0.3
