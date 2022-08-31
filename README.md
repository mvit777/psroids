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

