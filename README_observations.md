


Hockey2Rugby
=========================================

2 hrs on 980ti gives ~ 10K runs

## data used:
Hockey training data: Tampa Bay lightning (White uniform) vs Ottawa Senators (Red/black uniform)

Rugby training data:  France (Blue uniform) vs New Zealand (black uniform)


16k
=================================

First attempt:
Fields change colors

### result that seems to be occurring:
Blue France players seem to be transformed to white  (Mapping to tampa bay jerseys)
AllBlacks NewZealand players transformed into red (Mapping to Senators Jerseys)


32k
================================


##AtoB  HockeyVideo ---Rugby Transforming--->  RugbySTyle HOckey Rink   (GReen Ice)
32k Green Hockey Rink gets overtrained, starts becoming black
--- PRobably due to some training data being a closeup mash of allblack players (flesh and jersey)

Lots of blue appears in crowd

###BtoA   Rugby ----> Hockey Transform ---> Hockey style Rugby Field    (White grass)









64K
============================
Added more trianing data halfway through,
some with new colored RUGBY jerseys


#### Rugby w/ HockeyMod
When players cluster up, it thinks they are close to a net (A hihgly occurring scenario in the hockey footage)... So the color light blue appears on the ground (from the goal crease area), aswell as red goalposts.

Rugby players now have hockey sticks when moving at times !!!!!!!!!!!

#### Hockey w/ RugbyMOd

Less black patch anomalies than 32k.
There are now bright yellow patches, but this is from adding in new training data which contained yellow rugby jerseys.

As hoped for, the jerseys of the hockey players took on the new training data's jersey colors of Green/Red.



83K
===============================

#### Rugby w/ HockeyMod
Now Its really starting to get into hockey territory...
Model Learned how to map White/Blue Jerseys (Probably hard to do learning on a WHITE ice rink) onto rugby players.

At certain camera angles, its learned to make players bulky with hockey gear

The Hocket Net follows around clumps of players, like some weird phantom.

Just moved the overlay of original video to the other side to reveal that blasted
video watermark.



#### Hockey w/ RugbyMod

Yellow flashing around players was removed....
but pesky white logo type thing seems to be popping up more on the green ice.
Its the "Sky SPort" logo from the rugby training data.... it was conveniently placed
on the green turf for most of the rugby footage. Doh.
Hopefully It can train its way out this lol.





104 K
===================
Added some more data for both hockey and rugby, different color jerseys
DIfferent color Grass field.
At this point no major improvements seem to be happening, kind of 'scratching in the dark'

#### Rugby w/ HockeyMod

Getting more convincing on medium distance camera shots (most hockey training data for those)

Players look like they are skating with stick more often

Shots that are far away, which don't match scale of Hockey training data, confuse model, outputs only a 2-3 players whose size cover about 6-7 players from input frame.


#### Hockey w/ RugbyMod

Players now take on patches of 'flesh' on bottom.
Happened when I added a bunch of training data with closeup shots of players
with short shorts and big beefy legs lol.

Green Ice RInk flickers in color, probably due to introduction of differently
colored grass training data.

CLoseup of Goalie no longer is totally green, has patches of fleshy tone

Erasing crowd at top of shot with grass, probably due to lack of same shot angles with a rugby crowd (just grass in rugby!)


126 K
====================================
Add a bit more hockey data, closeup of blue jersey, see if it affects closeup of rugby players who are still just 'ice white skin'


#### Rugby w/ HockeyMod

@2s. Interprets helicopter shot at intro, _when no logo_, as weird closeup of hockey rink
@11s. Learnt how to display end of rink at starting shot of big field !

@21s - Wow player movement is smoooth!

@1.38 interesting sideboards morph

@1.54 OMG AWESOME! Its learned to somehow BEND the rink interpreting a Logo on the grass as the hockey audience.


#### Hockey w/ RugbyMod

Lots of blue and black

@17s. Net now has stripes

players are still followed by fleshy glow



144K
======================

#### Rugby w/ HockeyMod


#### Hockey w/ RugbyMod
Red glow around players skating ? ?


181K
==============

#### Rugby w/ HockeyMod

Net follows around clumps of players, zooms in/out of existence fluidly.

@36s.  Players up close take on some striping/start to look like hockey jerseys... 

@1:11. LOL Two goalie zones on the same end of rink, both with players around them (rugby posts)

@1:27 GOal posts interpreted as giant hockey players, players run in between the giants!

@2:25 LOl, NO NET at one end of rink




Just dense green fog, definitely ruined lol.


184K
===============
Quick checkin to see if messed up AtoB escaped weird tuning spot to better weights.

#### Hockey w/ RugbyMod
its getting worse. 
its now a weird pink & green watermelon candy land scene (The rabbitoh training data aughhh!), framed by an old fashioned green and blue painted picture frame lol.



201K
==================

Removed rabbitoh rugby training data..

#### Hockey w/ RugbyMod

Backing off a bit from weird picture frame (lost bottom border).


##### Rugby w/ HockeyMod

Overtraining, certain shots seem overly 'ham fisted' into hockey interpretation



232K
========================


#### Hockey w/ RugbyMod

Frame is back with a vengeance, its bigger, greener, and its contents are more pixelated , mostly green.
I say this AtoB conversion is a lost cause

##### Rugby w/ HockeyMod


Body tackle pileon closeups starting to take on a more 'Hockey' look as a jumble of red jerseys.

@1.13. Blending in that rink similar to 126K @1.54s

@1.54  Its unlearned  the "vignette" effect on the rink bend, so the rink no longer nicely 'blurs' as it bends to add to the believability. This time it has better learnt the edges so its a weird camera angle shift, suddenly seeing players in the background @1.56 

@2.05 LOl, finally replaced the AIG ad on the grass with TimHortons Red logo






264K
=================
ADded some top10 out%06d.jpg files to hockey, vignette effect, hoping to add a bit in


##### Rugby w/ HockeyMod
Ruined.   I suspect this is from reducing the training data to... 84 IMAGES. way to small probably.

#### Hockey w/ RugbyMod
Still Ruined.





321K
=======================
Add ton of training data to hockey, different jersey colors.
Add lots of original all blacks vs france training data to rugby, weird camera angles included, instead of epochs with batch size  84, it is now 3884.


##### Rugby w/ HockeyMod
Back from the dead! more of a grotesque.
@42s. Grotesque hockey Net machinations
Hockey players are too closeup, discerns a bunch of rugby players as just one big hockey player shambling sideways.


#### Hockey w/ RugbyMod
Slightly revived, blue somewhat discernable players on green.




382K
=====================
Added Allblacks vs south africa to rugby training data, same color green of field
Add 8000 knights vs Capitals to hockey training data


##### Rugby w/ HockeyMod

Big hockey 'stills' around ice, probably due to lots of data being more of a closeup.
Identifies crowd as just a big mesh of player bodies smushed together like a blurry escher bird drawing.

#### Hockey w/ RugbyMod

Picure is composed of small allblack players with a wierd mashed up score logo placed on the top of their bodies.
Frame still remains!




387K
=========================
Remove 95 % of Top 10 hockey training data, assume data had too many 'closeup' shots and messed with rugby input

Ran for 5K steps, with Learning Rate of 0.002 (10x normal)...
Success! ALthough I suspect learning rate could've been maybe a bit smaller, all the progress on the BtoA Rugby w/ HockeyMod seems to be lost.

##### Rugby w/ HockeyMod

reset progress back to beginning it seems, no frame border, players don't resemble hockey players.


#### Hockey w/ RugbyMod
 unlearnt the green frame border!!



428K
==========================
Learning Rate of 0.0003 (1.5x normal)

Wow! Hit a new level of accuracy  d_loss of 0.01.... weird


XK
===================
Back to normal learning rate 0.0002
