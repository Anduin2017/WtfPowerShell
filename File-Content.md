# File Content

I have a letter: `letter.txt`

```txt
Hi

My name is Anduin.

Bye
```

I read it:

```powershell
$myLetter=cat letter.txt
```

Seems fine:

```powershell
echo $myLetter

Hi

My name is Anduin.

Bye.
```

I check if it contains `Hi`:

```powershell
$myLetter.Contains("Hi");
```

The output is:

```PowerShell
True
```

But if I check if it contains `name`:

```powershell
$myLetter.Contains("name");
```

The output is:

```PowerShell
False
```

What a strange behavior of PowerShell! 😲

> Repro env: Windows 10, PowerShell Core 7.0.3