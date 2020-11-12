# Convert To Json strange behavior

Now you have an object with a collection.

```powershell
$myString = "12345"
$myObj = @{
    someOtherThing = @(
        @{
            collection = @($myString)
            property = "my property value"
        }
    )
}
```

Now convert that object to JSON.

```powershell
$myObj | ConvertTo-Json
```

Which outputs:

```json
{
  "someOtherThing": [
    {
      "collection": "12345",
      "property": "my property value"
    }
  ]
}
```

The collection is treated as a property which is wrong.

But if you do like this:

```powershell
$myObj | ConvertTo-Json -Depth 10
```

Which outputs:

```json
{
  "someOtherThing": [
    {
      "collection": [
        "12345"
      ],
      "property": "my property value"
    }
  ]
}
```

What a strange behavior of PowerShell!

> Repro env: Windows 10, PowerShell Core 7.0.3
