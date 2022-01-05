# From and To Json

Let's have an array in json:

```powershell
$ '[1, 2, 3]' | ConvertFrom-Json
```

Which outputs:

```powershell
1
2
3
```

Emmm. Pretty nice.

Let's convert it back!

```powershell
$ '[1, 2, 3]' | ConvertFrom-Json | ConvertTo-Json
```

Which outputs:

```powershell
{
    "value":  [
                  1,
                  2,
                  3
              ],
    "Count":  3
}
```

What a strange behavior of PowerShell! 😲

No... This is not ended yet...

If you try it this way:

```powershell
$myArray = '[1, 2, 3]' | ConvertFrom-Json
$myArray | ConvertTo-Json
```

Which outputs fine again:

```powershell
[
    1,
    2,
    3
]
```

Why????

What a strange behavior of PowerShell! 😲

> Repro env: Windows 11, Windows PowerShell 5.1.22000.282
