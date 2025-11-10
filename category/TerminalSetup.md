---
layout: category
title: Terminal
---

Powershell 5 is for babies and communists. 
Real developers run Windows Terminal with Powershell 7 and they pimp it out hard.

To get started you should already have Windows Terminal installed as they have been pushing it for a long time now.
If you don't have it yet you can get it from the Microsoft Store here: https://aka.ms/terminal

Click your start button type Terminal and it should come up.  Right click it and open as Administror.
<img width="667" height="354" alt="image" src="https://github.com/user-attachments/assets/9ba0ea29-82d8-4632-8f09-810e65c7e93b" />

Now we're going to install Powershell 7 via winget.  Type the following command and hit enter.

```winget install Microsoft.PowerShell```

<img width="479" height="218" alt="image" src="https://github.com/user-attachments/assets/ed0580a1-4ff3-40c7-84e2-2ed33c81c22f" />

That will ask for permission and do some stuff

<img width="1060" height="319" alt="image" src="https://github.com/user-attachments/assets/e027f46c-3800-4bee-9680-3abe21f6972d" />

<img width="1081" height="334" alt="image" src="https://github.com/user-attachments/assets/e6317746-57b1-419b-92b0-3c570bd96678" />

Click the dropdown arrow at the top of the terminal window and see if Powershell is there, if not you'll need to close and reopen terminal.

<img width="572" height="273" alt="image" src="https://github.com/user-attachments/assets/bac560c5-5fd1-4ef1-8f35-c6086dbf9945" />

ok now lets install oh my posh via winget 

```winget install JanDeDobbeleer.OhMyPosh```

<img width="539" height="159" alt="image" src="https://github.com/user-attachments/assets/8229dc9e-a296-4c3e-b330-104838ae46ff" />

Once that is done we can use it to install a special font, sometimes called a nerd font, which I hate but it is what it is.  I think FiraCode is a pretty good choice but you can obviously download a bunch and see what works best for you.

<img width="415" height="320" alt="image" src="https://github.com/user-attachments/assets/2ba8109a-3339-4d44-9e34-399fc78a59fa" />

When that is done lets pop into settings and make a few tweaks.  Click the dropdown next to the new tab button, click settings and lets change the default profile to Powershell, and make it match the screenshot.

<img width="375" height="305" alt="image" src="https://github.com/user-attachments/assets/be75ba14-6275-43c4-91b2-9c6dfb3eebfa" />

Then on the left click on Powershell and then on the right click on Appearance.

<img width="819" height="553" alt="image" src="https://github.com/user-attachments/assets/ec2ad643-0e2b-421d-b859-cd96468b5126" />

<img width="778" height="529" alt="image" src="https://github.com/user-attachments/assets/6e51d393-63c9-414e-ab03-7dd474b57c73" />

We want to set the color scheme to One Half Dark, set the font face to FiraCode Nerd Font Mono and kick the font size up a bit.

<img width="792" height="642" alt="image" src="https://github.com/user-attachments/assets/fbe6cb70-d9a7-4833-9fda-46b3612d09d3" />

<img width="768" height="489" alt="image" src="https://github.com/user-attachments/assets/528c6a96-2d37-423c-b10f-0962d9725edb" />

Ok, now we'll install some terminal icons via Powershell.  Open a new Powershell tab and run the following command:
```Install-Module -Name Terminal-Icons -Repository PSGallery```

<img width="1082" height="207" alt="image" src="https://github.com/user-attachments/assets/f3f33223-12c4-4931-ae97-c69bcb16ff78" />

Create a folder in your Documents folder called PowerShell 

<img width="315" height="294" alt="image" src="https://github.com/user-attachments/assets/c5b4ec5a-69d6-4ad2-8e32-2dc80dd86357" />

Put the attached file Microsoft.PowerShell_profile.ps1 into it but remember to fix the path inside. 
[Microsoft.PowerShell_profile.ps1](https://github.com/Echostorm44/NewPcInstallStuff/blob/main/TerminalPimping/Microsoft.PowerShell_profile.ps1) 
The contents of the file are:
```powershell
oh-my-posh --init --shell pwsh --config C:\OhMyPoshTheme\AdamCustom.json | Invoke-Expression
Import-Module -Name Terminal-Icons
[console]::InputEncoding = [console]::OutputEncoding = [System.Text.UTF8Encoding]::new()
```

<img width="351" height="218" alt="image" src="https://github.com/user-attachments/assets/916c1478-4dc6-4d6c-9979-e38f0b019087" />


I have a pretty great custom theme you can [download](https://github.com/Echostorm44/NewPcInstallStuff/blob/main/TerminalPimping/AdamCustom.json)

<img width="463" height="175" alt="image" src="https://github.com/user-attachments/assets/6f1cee45-25fa-4734-a9bc-a2cd2e0413ee" />

Or you can be lame and use one if the ones they have posted.  See here: 
https://ohmyposh.dev/docs/themes

With that done one way or another you'll need to run this:
```powershell
Unblock-File -Path $PROFILE
```

<img width="410" height="102" alt="image" src="https://github.com/user-attachments/assets/4c2a14f6-d271-42c7-8195-797e133e580f" />


Once that is all complete you should be able to open a new tab and it should look glorious


<img width="1592" height="708" alt="image" src="https://github.com/user-attachments/assets/e440b8a3-6c3e-4808-a2b1-7f3e09691e52" />


For cmd.exe, which you'll still need from time to time, the following steps are required to enable Unicode and Emoji support.

Run intl.cpl.
Click the Administrative tab
Click the Change system locale button.
Check the "Use Unicode UTF-8 for worldwide language support" checkbox.
Reboot.
