# Intro
PowerShell is object-oriented. Its commands are known as cmdlets (command-lets) they follow a Verb-Noun naming convention meaning the `Verb` describes the action and the `Noun` specifies the object on which the action is performed. For example:

`Get-Content`: retrieves (gets) the content of a file and displays in the console

`Set-Location`: changes (sets) the current working directory
## Basic Cmdlets
`Get-Command`: returns all available cmdlets, functions, aliases and scripts that can be executed in the current PowerShell session, with command-type, name, version and source.
Its possible to filter the list of commands based on displayed property values, for example:

`Get-Command -CommandType "function"`

`Get-Help [cmdlet]`: which provides detailed information about cmdlets, including usage, parameters and examples. Go-to for learning how to use PowerShell. For example:

`Get-Help Get-Date` returns helpful information about the `Get-Date` cmdlet.
Additionally we can append options/properties to the basic command:
`Get-Help Get-Date -examples`

`Get-Alias`: returns popular aliases which are shortcuts or alternative names for cmdlets. For example:

`cd -> Set-Location` 

You can also download additional cmdlets from online repositories. We can use `Find-Module` if we dont know the exact name of the module we can search for modules with similar names this can be done following the Powershell standard syntax: `Cmdlet -Property "pattern*"` - for example:

`Find-Module -Name "Powershell*"`
Once the module is found, say we want the module `PowerShellGet` we can do:
`Install-Module -Name "PowerShellGet"`
## Navigating the File System and working with files
Similar to `dir` in the cmdprompt or `ls` in unix.like systems, `Get-ChildItem` lists the files and directories in a location specified with the `-Path` parameter. It can be used to explore directories and view their contents. If no `Path` is specified, the cmdlet will display the content of the current working directory.

`Set-Location` is our navigation command, similar to the `cd` command in cmdprompt.
Again we need to specify the `-Path` property, so the command to navigate to .\Documents would be: `Set-Location -Path ".\Documents"`

To create a new item in PowerShell, we can use the `New-Item` command. This is similar to the `mkdir` command in cmdprompt, but its much more capable and general, as it can create any "item". The `mkdir` lookalike-command would be:

`New-Item -Path ".\universe\alternateUniverse" -ItemType "Directory"`
And if we wanted to make a file:

`New-Item -Path ".\universe\alternateUniverse\myUniverse.txt" -ItemType "File"` 

Similarly if we want to remove an item, we use `Remove-Item`, this can both act like the `rmdir` and `del` command. 

`Remove-Item -Path ".\universe\alternateUniverse\myUniverse.txt"`

`Remove-Item -Path ".\universe\alternateUniverse"`
## Network in PowerShell
Test network connection to verify reachability:

`Test-NetConnection -ComputerName [ip] -port [port]`

`Test-NetConnection -ComputerName 192.168.1.145`

`Test-NetConnection -ComputerName 192.168.1.145 -Port 3080`