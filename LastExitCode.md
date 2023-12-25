# Last exit code

Last exit code represents the exit code of last command.

```powershell
ping bing.com
$LastExitCode
```

And you will see:

```powershell
0
```

Which means the last command `gcm help` finished successfully.

If you ping something that does not exist, you will see:

```powershell
ping aaaaaa
$LastExitCode
```

And you will see:

```powershell
1
```

Emmm. Good. Exit code 0 means success and exit code 1 means failure.

Now you learned that, let's try this:

```powershell
gcm help
```

And you will see:

```powershell
$LastExitCode
0
```

But if you try:

```powershell
gcm xxxxxxxxxxx
gcm : The term 'xxxxxxxxxxxxx' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ gcm xxxxxxxxxxxxx
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (xxxxxxxxxxxxx:String) [Get-Command], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand
```

However, now the `$LastExitCode` is still `0`!

```powershell
$LastExitCode
0
```

What a strange behavior of PowerShell! 😲
