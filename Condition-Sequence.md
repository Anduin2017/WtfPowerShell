# Condition sequence

Now we have some fruit.

```powershell
$fruits = @('Apple','Orange','Banana')
```

Of course, `Apple` is a fruit. Not `fruits`:

```powershell
if ('Apple' -eq $fruits) {
    echo 'True!'
} else {
    echo 'False!'
}
```

Which outputs:

```text
False!
```

But is `$fruits` Apple?

```powershell
if ($fruits -eq 'Apple') {
    echo 'True!'
} else {
    echo 'False!'
}
```

Which outputs:

```text
True!
```

What a strange behavior of PowerShell!

> Repro env: Windows 10, PowerShell Core 7.0.3
