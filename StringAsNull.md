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
$ ([string]($null)).Count
1
$ ($null).Count
0
```
