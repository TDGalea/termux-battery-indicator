# Termux Battery Indicator
Prints the battery percentage and charging status.<br />
Designed for use within XFCE's panel in a generic monitor (genmon).<br />
While `xfce4-battery-plugin` can be installed and works, in my use-case it was <i>extremely</i> sluggish - even the config window was unusable. I'm gonna take a guess and say it's abusing the Termux:API way too frequently.


## Dependencies:
### Android:
<a href="https://f-droid.org/en/packages/com.termux.api/">Termux-API</a> must be installed.
### Termux environment:
`termux-api` and `jq` are required.
### XFCE:
`xfce4-genmon-plugin` is used to display the script output inside the panel.

## Installation:
Just download the script and put it somewhere accessible by Termux.<br />
(Or better yet, just download it within Termux in the first place).

Personally, I've got it in `/data/data/com.termux/files/usr/bin/`.

Then, if you want to add it to the XFCE panel, add a Generic Monitor (genmon) item and point it at this script.<br />
As an example, below is my own genmon config:<br />
```
Command: /data/data/com.termux/files/usr/bin/batlvl
Label: OFF
Period (s): 30.00
Use a single panel row: ON
Font: DejaVu Sans Book 10
```
Period can be more frequent, but it would be kind of pointless in my opinion. I wouldn't go lower than 15s though.<br />
The font can be whatever you like. As far as I can see, emojis aren't font-dependent, so go wild.

## Examples:
\> 20%, discharging:<br />
<img width="367" height="288" alt="image" src="https://github.com/user-attachments/assets/d28d302a-7c95-4288-a7f8-933fb7311d42" />
<br />
< 20%, discharging:<br />
<img width="367" height="288" alt="image" src="https://github.com/user-attachments/assets/478f9740-cae0-4a4e-b945-28a964105644" />
<br />
Any%, charging:<br/>
<img width="367" height="288" alt="image" src="https://github.com/user-attachments/assets/600e0463-4664-4ac4-8683-47fae8cad216" />

As shown in the second two screenshots, you can test any percentage and state directly by using the `-t` parameter:<br />
`batlvl -t 20` will print 20%, emoji representing actual state.<br />
`batlvl -t 69 CHARGING` will print 69% with a plug emoji.
`batlvl -t 5 DISCHARGING` will print 5% with a low-battery emoji.
