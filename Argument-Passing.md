# Argument passing

Now we have a function

```powershell
function MyFunction ([string[]]$mylist, [string] $mystring) 
{
    Write-Host $mylist.Count
    Write-Host $mystring
}
```

This function will output the list, and then output my string.

And declare some variables:

```powershell
$something = "something"
```

Call our function with null:

```powershell
MyFunction($null, $something);
```

Guess the output?

Outputs:

```text
2
```

Where is my 'something'? Where does the `2` comes out!?

What a strange behavior of PowerShell!

> Repro env: Windows 10, PowerShell Core 7.0.3
