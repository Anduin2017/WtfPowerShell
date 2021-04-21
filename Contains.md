# Contains

Consider the following snippet:

```powershell
"12-18" -Contains "-"
```

You’d think this evaluates to true.

But it doesn't. This will evaluate to `false` instead. 

I’m not sure why this happens, but it does.

But if you try:

```powershell
"12-18".Contains("-")
```

Now the expression will evaluate to $true.

What a strange behavior of PowerShell! 😲
