# Space after `

Now we have a and b.

```powershell
$a = $true;
$b = $false; 
$aAndB = $a -and $b

return $aAndB;
```

Which outputs `False`. Very correct.

Now make that command to two lines.

```powershell
$a = $true;
$b = $false;
$aAndB = $a `
    -and $b

return $aAndB;
```

Which outputs:

```text
False
```

But if you add a space after

> `

```powershell
$a = $true;
$b = $false;
$aAndB = $a ` <---- There is a space here
    -and $b

return $aAndB;
```

Which outputs:

```text
True
```

What a strange behavior of PowerShell!

> Repro env: Windows 10, PowerShell Core 7.0.3
