# Not false is false?

I was testing a file version.

So I wrote this:

```powershell
"10.0.22000.1" -like "11.0.*"
```

Of course, the output is:

```text
False
```

Em. I like it.

So I kept developing... And I added a `-not`.

```powershell
-not "10.0.22000.1" -like "11.0.*"
```

Since `-not False` must be `True`.

But the result I got is:

```text
False
```

What a strange behavior of PowerShell! 😲

> Repro env: Windows 11, PowerShell Core 7.0.3
