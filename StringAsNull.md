In PowerShell, if you convert `null` to `string`, it will become an empty string.

```powershell
$ ([string]($null)).GetType()

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     True     String                                   System.Object
```

If you output it:

```powershell
$ ([string]($null))

$ ($null)
$
```

If you get the count:

```powershell
$ ($null).Count
0
$ ([string]($null)).Count
1 # Now it has a count after you converting that `null` to `string`.
```

Event more:

```powershell
$ [int]$something = $null
$ $something -eq $null
```

Which outputs:

```
False
```

What a strange behavior of PowerShell! 😲
