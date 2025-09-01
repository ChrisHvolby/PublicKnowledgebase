# Windows PowerShell
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
`New-Item -Path ".\captain-cabin\captain-wardrobe" -ItemType "Directory"`
And if we wanted to make a file:
`New-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt -ItemType "File"` 

Similarly if we want to remove an item, we use `Remove-Item`, this can both act like the `rmdir` and `del` command. 
`Remove-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt"`
`Remove-Item -Path ".\captain-cabin\captain-wardrobe"`




## Network in PowerShell
Test network connection:
`Test-NetConnection -ComputerName [ip] -port [port]`
`Test-NetConnection -ComputerName 192.168.1.145`
`Test-NetConnection -ComputerName 192.168.1.145 -Port 3080`
# Windows CMD
## SSH Remote Connection to CMD (SSH)
Secure network-protocol, offering encrypted connection to remote pc’s offering administration capabilities, typically used to connect/log into a remote computer's shell or command-line interface (CLI). 
Syntax: >`ssh [username]@[IP]`
"Confirm prompt" >`yes`
"Enter password" >`[password]`

---

## CMD Basics
- Show path: `set`
- OS version: `ver`
- System info: `systeminfo`  
  - Page by page: `systeminfo | more`
- Help: `[command] -h` or `[command] /?`

---

## CMD Networking
- Show IP config:  
  - `ipconfig`  
  - `ipconfig /all`
- Ping: `ping [target]`
- Trace route: `tracert [target]`
- Lookup host/domain:  
  - `nslookup example.com`
  - `nslookup example.com 1.1.1.1`
- Connections and ports: `netstat`  
  - Options:  
    - `-a` (all)  
    - `-b` (show programs)  
    - `-o` (show PID)  
    - `-n` (numerical)  
  - Example: `netstat -abon`

---

## CMD File & Disk Management
- Change dir: `cd [dir]`
- Go up one level: `cd ..`
- List dir: `dir`  
  - `dir /a` (hidden/system)  
  - `dir /s` (recursive)
- Tree view: `tree`
- Create dir: `mkdir [name]`
- Delete dir: `rmdir [name]`
- Show file contents: `type file.txt | more`
- Copy file: `copy test.txt test2.txt`
- Move file: `move file.txt C:\target`
- Delete file: `del file.txt` or `erase file.txt`
- Wildcard: `copy *.md C:\Markdown`

---

## CMD Tasks & Processes
- List processes: `tasklist`
- Filter by image: `tasklist /FI "imagename eq sshd.exe"`
- Kill by PID: `taskkill /PID 4567`

---

## CMD Common Useful Commands
- Check disk: `chkdsk`
- List drivers: `driverquery`
- Scan/repair system files: `sfc /scannow`

---

## Shutdown
- Shutdown: `shutdown /s`
- Restart: `shutdown /r`
- Abort: `shutdown /a`
