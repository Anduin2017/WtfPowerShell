# Null is not null

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

What a strange behavior of PowerShell! 😲
