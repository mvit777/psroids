# PSCardsRage

## Antefact
I'm expanding my powershell knowledge, as such I did not want a trivial bunch of scripts to work with and I came up with this absolutely insane project.
It does a lot of crazy stuff and along the way it sends cards to MS Teams channels.

## Facts
I stumbled across this [curated list of powershell resources](https://github.com/janikvonrotz/awesome-powershell) and my attention was caught by [this awesome library](https://github.com/EvotecIT/PSTeams) that sends cards to MS Teams. The library is supercool and works like charm but since I don't like to pass too many and too elaborated params on the command line, I start figuring out a simplier way to call the api and defining the content.
In my taste the following line is a bit verbose to be issued with ease on the commandline.

```powershell
New-ThumbnailCard -Title 'Bender' -SubTitle "tale of a robot who dared to love" -Text "Bender Bending Rodríguez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio" {
    New-ThumbnailImage -Url 'https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png' -AltText "Bender Rodríguez"
    New-ThumbnailButton -Type imBack -Title 'Thumbs Up' -Value 'I like it' -Image "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg"
    New-ThumbnailButton -Type openUrl -Title 'Thumbs Down' -Value 'https://evotec.xyz'
    New-ThumbnailButton -Type openUrl -Title 'I feel luck' -Value 'https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE'
} -Uri $Env:TEAMSPESTERID
```
What I came up with is a powershell script that reads the above parameters from a json file (actually it is a yaml file that get automatically translated into json). It allows a user to specifiy interactively:
- type of card
- edit configuration file for the contents
- to optionally use a blazor GUI to customise the contents or edit them directly in vscode
- list of channels you want to send the card to 

In its basic form, it started and ended with a powershell script, a bunch of custom modules, the above mentioned module PsTeams and C# library wrapper which I inkvoke directly from the powershell script.
When it came to adding the GUI things got more complicated but also more interesting. In fact, I had to add a blazor wasm app and a webservice.

While the structure of the project is a bit convoluted I can assure you that it allows a user of any technical skill to send cards to a MS Teams in a matter of seconds and in a funny way.

## A few pictures of how it looks like at his full strength
You just invoke with no arguments
```powershell
PS C:\Bin\Teams-Messenger> .\main.ps1
```
answer a couple of quick interactive questions
```powershell
PS C:\Bin\Teams-Messenger> .\main.ps1

choice
select type of card
[A] Adaptive  [L] List  [H] Hero  [T] Thumbnail  [?] Help (default is "A"): t
Select the channels you want to send the card
Taxonomy General
Confirm
Use blazor gui to edit config file?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```
and you create the card with the GUI, choose one or multiple channels and send the card
![gui](https://github.com/mvit777/psroids/blob/main/img/psroids_at_full.png)

and this is what you get...
![teams](https://github.com/mvit777/psroids/blob/main/img/teams.png)

## The Workflow

## More in deep
As said the project has a lot of crazy dependcies and a bit of configuration (mainly Teams itself).
As far as the deps are concerned here a briefly schetched list:
- PsTeams
- TeamsModule
- System.Management.Automation
- Setting up each channel with office connector
- Powershell.cmdlet c# library
- blazor-client.dll
- backend.dll
- bin folder with only
    - ranx.common folder
    - team-messenger folder

Obviously it is too much junk to be usable in this state and a build & configure script is very much needed.
As soon it is ready I will release the rest of the code.
But basically all the meat is in the powershell script itself and in the C# lib that handles the send command.
The rest is just regular Blazor wasm + web service.

The most notable thing is that the script runs smoothly inside vscode so I'm in doubt wheter to turn everything 
into a single compact .exe or not. I admit that it looks tempting....


(coming soon...)
