# Condition sequence

Now we have some fruit.

```powershell
$fruit = @('Apples','Oranges','Bananas')
```

And write a simple method:

```powershell
if ($fruit -eq 'Apples') {
    echo 'True!'
} else {
    echo 'False!'
}
```

Which outputs:

```text
True!
```

But if you invert the condition:

```powershell
if ('Apples' -eq $fruit) {
    echo 'True!'
} else {
    echo 'False!'
}
```

Which outputs:

```text
False!
```

What a strange behavior of PowerShell!

> Repro env: Windows 10, PowerShell Core 7.0.3
