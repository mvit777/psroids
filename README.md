# PSRoids

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

## More in deep
(coming soon...)
