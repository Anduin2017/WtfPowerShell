# Null is not null

When you have something which is null:

```powershell
$ [int]$something = $null
```

And test it with eq:

```powershell
$ $something -eq $null
```

Which outputs:

```
False
```

What a strange behavior of PowerShell! 😲
