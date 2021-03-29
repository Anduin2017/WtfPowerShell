# Guess my type

Let's have an array:

```powershell
function GetArray()
{
    $myArray = @("apple", "banana")
    return $myArray
}
$array = GetArray
$array.GetType()
```

Which outputs:

```powershell
IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     True     Object[]                                 System.Array
```

The type is: `System.Array`.

But when you only return one element:

```powershell
function GetArray()
{
    $myArray = @("apple")
    return $myArray
}
$array = GetArray
$array.GetType()
```

Which outputs:

```powershell

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     True     String                                   System.Object
```

The type became: `System.Object`.

What a strange behavior of PowerShell! 😲
