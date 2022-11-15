# Return value

Now we have a function:

``` powershell
function Calculate {
    echo "Doing some calculation..."
    return 1 + 2
}

$result = Calculate
```

Guess what would its return value `$x` be? 

A `int` with value `3`?

Of course... **NOT**!

It actually returns an array, containing a `string` and an `int`.

```powershell
> $result
Doing some calculation...
3

> $result.GetType()

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     True     Object[]                                 System.Array
```

The return value of a PowerShell function would be all the return values of the sub-functions called by this function. The `return` keyword does nothing other than terminating the function execution. This is by design.

If yoy don't wish the return value of a sub-function to be included, be sure to guard it with `Write-Host` or `Out-Null`.
