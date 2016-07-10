#biscottiCFG
v. 1.05

This is my personal config for Team Fortress 2 (TF2).

**Table of Contents**
* [What are scripts, though?!](#what-are-scripts-though)
* [Installation](#installation)
* [Features](#features)
  * [All-Class](#all-class)
  * [Scout](#scout)
  * [Soldier](#soldier)
  * [Pyro](#pyro)
  * [Demoman](#demoman)
  * [Heavy](#heavy)
  * [Engineer](#engineer)
  * [Medic](#medic)
  * [Sniper](#sniper)
  * [Spy](#spy)
* [Close Captions](#close-captions)
* [Credits](#credits)
* [See it in action! YouTube!](#see-it-in-action-youtube)

#[^](#top "Back to Top")What are scripts, though?!
Scripts aren't cheats. They're basically just really fancy keybinds that personalize how you control the game. Some are simple, say you want to bind `slot2` to e, that's really easy to do. But some require a lot of scripting logic to pull off. Say you want to tell your team when you throw a sandvich, and then immediately switch to your minigun after throwing it, that's definitely possible, but it's much more complicated.

I made a [YouTube video](https://youtu.be/FgiyDK5JVS4 "TF2: Explaining Scripts and Scripting [NOT Cheats!]") on my channel a while back that explains this in greater detail. It's 5 minutes long so it's just a cursory glance at the subject but it explains in general terms what scripting as a whole is about.

#[^](#top "Back to Top")Installation
Click the button that says **Download ZIP**.

Then extract it to your `/tf/custom/` folder so that inside your custom folder there is a folder called **biscottiCFG** which contains `cfg` and `resource`.

#[^](#top "Back to Top")Features
This is the main bulk of the readme and is divided into 10 sections based on the relevant classes (the 9 + All-Class). There are a lot of features in my config, so this is going to be quite long and might look disorganized. I'll make a brief explanation of what's happening in the config at the start of each section and conclude it with a table that shows the different keybinds to the different functions and what they do. I sincerely apologize if I miss anything. There's tons of stuff as it is, and who knows what I might add in the future.

Good luck!

##[^](#top "Back to Top")All-Class
This section has all the stuff that's common for all the classes like weapon switching, movement, and several other binds and scripts, like team calls on the keypad and inventory binds.

**Weapon switching**

Obviously, you've got all the normal stuff like *number keys*, *mousewheel*, and *Q* for switching to the last weapon. In addition to that, I use the *thumb buttons* on my mouse to switch weapon 99 % of the time. I also wrote different systems for switching weapons using the thumb buttons and mousewheel. A normal mouse only has two thumb buttons so a more advanced and complicated system is required, my mouse, however, has three buttons specifically because this is my main method of switching weapons. The extra mouse button is bound to `'` in TF2 (apostrophe). For the public release of the config I'll make one of the two-button presets the default one.

The system for changing weapons can be edited or changed to a different one collectively in the `STOCK SELECTIONS` section of `autoexec`, or on a per class basis by putting `alias mw_pres mw_orig` or something similar followed by `mw_pres` somewhere in the class config. Preferable at the end but before the part that says `eq_1` ( or `eq_2` in the case of Medic).

It should also be noted that the weapon switch systems has some flaws because it can't *see* what weapon you have out, instead it has to *approximate* the weapon slot based on your button presses. This can lead to de-syncs in fringe cases, but those are for the most part meaningless and also easy top fix by just inputting another weapon switch command. Read more on the limitations [here](https://www.reddit.com/r/Tf2Scripts/comments/42copn/two_script_requests3/cz9zsd7 "Reddit comment").

It's this system that allows different scripts and settings to be applied to different slots.

I should also mention that I use this to change crosshairs, but these can be edited in the class configs and in the crosshairs own config files. The separate files are for the actual commands involved in the crosshair. The class config is to actually switch between them.

**Movement**

`WASD`. D'uh! Seriously, though, it's really complicated. I don't even fully understand it and I wrote the damn thing!

You've got your basic null-movement script which basically means that instead of stopping all movement when you down both strafe keys, `A-D` (same goes for `W-S`), you will move in the directing you last pressed, and when you release it, you return to moving in the direction of the button you pressed first.

I also wrote a *REALLY* complicated autorun function. Basically, when you hold `ALT` and press `R`, you'll start running automatically and the `A-D` turns into a steering wheel to turn your character. When you hold `CTRL` in this mode, it turns the steering into air strafing. This is useful for controlling your movement in the air, just make sure to hold CTRL while doing it (let's be real, that's usually what you do anyway). Pressing forwards or backwards will stop the autorun (`W-S`).

**Attacking**

Attacking with most hitscan weapons (bullets) will hide the viewmodel to give you a better view of the screen and ideally a clearer aim on your target. Holding `ALT` while firing will negate this behaviour.

Again, this is tracked on a per slot basis based on your button presses, so if you use the Gunboats, the script will still think you have the shotgun equipped and will consequently hide the viewmodel when you try to attack with it (only if you've pressed to go to `slot2` but this includes the mousewheel).

To combat this I've made different *loadout preset settings* that apply when you use the `KEYPAD` bind to switch loadout (this can be disabled pretty easily. See below). These will try their best to act according to the problematic weapon in the loadout. E.g. not hiding the viewmodel when switching to gunboats and ignoring the change to the crosshair. The mousewheel will still try to switch to `slot2`, so it will take 2 clicks to get from the melee to the primary, but at least it won't mess up the script settings. The specific setting being applied by default is set at the bottom of the class config with the others commented out.

*NOTE: I've made changes to how I deal with Gunboats and it should work properly now, so that the mousewheel skips over slot2 (see the Soldier, Demoman, and Sniper configs for more detail).*

You can disable the automatic switching between presets when using the `KEYPAD` to switch loadouts by using the aliases `loadoutpresets_1` and `loadoutpresets_0`. These are stated at the bottom of each relevant class config in the `SELECTIONS` section. If you disable it, you should still put the preferred preset in the same section. They all there, but the disabled ones are commented out.

What weapon slots that do or do not hide the viewmodel can be changed in the class configs. As a general rule you can change them by changing the part `alias vm_def vm_#` in the `slot_` aliases, where `#` is a `1` or `0` (`1` is viewmodel on, `0` is viewmodel off when attacking).

**Team calls**

These are the helpful parts of the config. Basically just a quick way to alert your team of your enemies movement/status.

You can call out what class the enemy spy is currently disguised at by holding `ALT` and pressing the `NUMBER KEY` corresponding to the class you want to call. E.g. `ALT + 3` = "Spy is Pyro!"

`ALT` + the numbers on the `NUMPAD` (referred to as `KEYPAD` because I have no regard for consistency) will call out which class is dead. Can also be used to call when the enemy team pops Über, when the sentry goes down, and when you have an advantage in numbers. E.g. `ALT + KEYPAD 7` = "Medic down!"

**Stupid loops/mousewheel binds**

So this is the derpy part of the config. I've meticulously designed loads of different ways to pass time in setup with these spam-scripts (NOT THE CHAT!). What they do is just very quickly repeat a short sequence of commands which will hopefully look stupid and amuse some people. If `wait` is enabled on the server, it will automatically set them to be loops, and if `wait` is disabled, it will set it to be mousewheel binds because those are easy to spam.

Some of these are bound to keys, typically the `NUMPAD` (`KEYPAD`).

They are:

| Aliases		| Key		| Description																				|
|:------------- |:--------- |:-----------------------------------------------------------------------------------------	|
| `derpmove_t`	| KEYPAD 1	| Moves back and forth really quickly. The goal is to make a feet shuffling motion.			|
| `brutal_t`	| KEYPAD 2	| Spams the taunt in the second Taunt slot. Please make sure that it's the Shread Alert. It also changes your loadout to B because that's where I have my Saharan Spy set which adds the sandstorm effect. |
| `pootis_t`	| N/A		| Spams the voice command "Dispenser Here!". The goal is to make the Heavy say "Pootis".	|
| `dwep_t`		| KEYPAD 3	| Rapidly switches through your weapons. On spy this will also change your disguise weapon.	|
| `jump_t`		| KEYPAD DEL | Makes you jump. 'Nuff said. Has funny interaction with the Base Jumper (Parachute).		|
| `shake_t`		| N/A		| Makes you shake your head rapidly from side to side.										|
| `freak_t`		| N/A		| Shakes and shoots your weapon. Not entirely sure why I made this. It also doesn't have a mousewheel version. |

**Help**

I've made a few `help` aliases in case you forget what some of the settings and aliases are called. There aren't very many of them but they might come in handy.

| Aliases					| Description |
|:------------------------- |:----------- |
| `help_crouch`				| Will tell the aliases to put in to switch between crouch/`duck` on `CTRL` or `SHIFT`. The aliases are `ctrlcrouch` and `shiftcrouch`. I use `CTRL`. |
| `help_class`				| Will explain different class-specific scripts and controls. Will also list loadout preset settings. |
| `help_loadout`			| Will explain how to enable/disable automatically switching presets with the loadout buttons. `loadoutpresets_t`, `loadoutpresets_1`, `loadoutpresets_0`, and `alias loadoutpresets_n loadoutpresets_0` to disable for all classes. |

**Demo recording and rendering**

I use P-REC to record demos, but I've also bound a few keys to make it easier. I also made a config that enables my demo rendering settings and allows for using aliases/binds to start the recording process. I found that this removed an audio desync issue that I was experiencing before.

I've also included my own P-REC settings that you might want to change. You'll find them in `autoexec.cfg` under the `P-REC` section at the bottom of the file.

`ALT + SEMICOLON` is used to start the demo recording using P-REC. After that, pressing `SEMICOLON` will bookmark that point in the demo recording and ensure that the demo file doesn't get deleted. By default, all demos that don't contain bookmarks or notable killstreaks (kills in a short amount of time, *I think*) will get deleted automatically. This can be changed in the P-REC section of the config (change `prec_delete_useless_demo 1` to `prec_delete_useless_demo 0`).

`record_demo.cfg` is the file for rendering demos. What you want to do is load up the demo, then put `exec record_demo` in console. The config will then echo instructions in the console on how to render the demo. It'll say this:

```
To start recording, type 'alias movie 'startmovie **title** h264'', close the demoui and hit L.
Type "alias r_drawviewmodel" in order to always have viewmodels on.
To re-enable viewmodel scripts, restart TF2.
```

**Sensitivity, FOV, volume, and other stuff**

In the `STANDARD SETTINGS` part of in `autoexec.cfg` you'll find a lot of normal settings for TF2 including my sensitivity, FOV, viewmodel FOV, and volume. You can change all these settings as you please.

Currently I use: `viewmodel_fov 70`, `sensitivity 2.66`, and `volume .04`, and voice chat disabled.

**Nightmare**

*CURRENTLY NOT INCLUDED IN THE CONFIG. I'm going to keep it to myself for a little while.*

This is by far the stupidest thing I've ever written. And believe me, I've written a lot of dumb shit. This takes the cake.

Basically, type in `nightmare_1` in console to activate *Nightmare Mode*. It's a client-side scripting game mod that I wrote for fun. What it does is activate a loop that periodically throws a random modifier into the mix that you have to deal with. It's just for messing with yourself and making your own life more difficult for fun. You can activate the loop multiple times to make it throw annoying stuff at you more often.

Note that it uses the `wait` command to do pretty much everything, so you might have to tweak the `wait` values to suit your own framerate, seeing as the amount in real-time that the command waits is  tied to your framerate. It is therefore unreliable to do exact timing, but luckily I have no need for exact timing, just know that most of the nuisances last about 10 seconds. Also note that `wait` has to be enabled on the server (`sv_allow_wait_command 1`) otherwise it'll probably crash your game, so please make sure that the server allows it. For reference, Valve servers allow `wait` but some community servers don't. I've used a *wait tester* to make sure that you only activate it when it's allowed, but still, take care.

Type `nightmare_0` to deactivate all the nightmare loops.

**All-Class features in a table**

| Binds						| Description																				|
|:------------------------- |:-----------------------------------------------------------------------------------------	|
| `WASD`					| Null-movement																				|
| `ALT + R`					| Auto-run. Turns `A-D` into a steering wheel. `CTRL + A-D` is air strafe.					|
| `ALT + [NUMBER KEY]`		| Say in team chat: "Spy is [Corresponding Class]!"											|
| `ALT + E`					| Ask for Über-Charge.																		|
| `ATTACKING with HITSCAN`	| Hides the viewmodel when shooting. See the specific classes for more info. Switching weapons brings it back. |
| `ALT + ATTACKING`			| Disables this feature. The viewmodel stays on the screen for as long as you hold `ALT`.	|
| **KEYPAD**				|																							|
| `KEYPAD 4, 5, 6, PLUS`	| Changes loadout. Also enables certain presets depending on class. Those can be removed.	|
| `KEYPAD 1, 2, 3, DEL`		| Toggles some stupid loop binds. If `wait` is not enabled, it uses the mousewheel instead.	|
| `KEYPAD 9`				| `hud_reloadscheme`. Use it if the HUD is broken or while editing the HUD.					|
| `KEYPAD ENTER`			| Kill bind. Explode actually. Just for good measure.										|
| `ALT + KEYPAD 1-9`		| Say in chat: "[Corresponding class] down!"												|
| `ALT + KEYPAD PLUS`		| Say in chat: "Sentry down!"																|
| `ALT + KEYPAD 0`			| Say in chat that you have numbers and that they should push.								|
| `ALT + KEYPAD DEL`		| Say in chat that the enemy team popped Über and that they should retreat.					|
| **LOADOUT + INVENTORY**	|																							|
| `CTRL + N`				| Item Quickswitch toggle. Press `N`, `CTRL + N`, or `ALT` to close it again.				|
| `M`						| Loadout Screen																			|
| `CTRL + M`				| Inventory Screen																			|
| **MISC**					|																							|
| `Z, X, C`					| Concise Voice Menus. Use slots `1`, `2`, `3` to navigate the voice commands. Ex. `Z12` = Thanks!	|
| `ALT`						| ALT by itself resets most scripts, like enabling the viewmodel again and stopping loops.	|
| `F11`						| Shows the contract drawer. At some point Valve changed it to F2 but I like it on F11.		|
| `CTRL + TAB`				| Brings up the Scoreboard with mouse mode enabled. Mouse mode is disabled by default.		|
| **DEMO RECORDING**		|																							|
| `ALT + SEMICOLON`			| Starts a demo recording with P-REC.														|
| `SEMICOLON`				| Bookmarks that point in the demo using P-REC.												|

| Aliases					| Description																				|
|:-------------------------	|:-----------------------------------------------------------------------------------------	|
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |
| `regen_on`				| Enables REGEN. Make sure that the server has `sv_cheats 1` and `sv_allow_wait_command 1`.	|
| `regen_off`				| Disables REGEN.																			|
| `nightmare_1`				| Activates *Nightmare Mode* to make your life more difficult for fun. Welcome to the real world, maggot. *CURRENTLY NOT INCLUDED THE CONFIG* |
| `nightmare_0`				| Deactivates *Nightmare Mode*. Welcome back to kindergarten. *CURRENTLY NOT INCLUDED IN THE CONFIG* |

##[^](#top "Back to Top")Scout
The Scout config is currently a bit broken, so one part of the script is disabled and has to be re-worked quite a bit, and honestly I really dislike that script anyway. Other than that, the loadout preset settings should work fine.

`help_class` will list the loadout preset aliases. You can change what loadouts get what setting in the `PRESETS` section. You can see how to disable the automatic preset switching by using `help_loadout` (`loadoutpresets_1` and `loadoutpresets_0`). Even if you disable it, you should still put the preferred preset at the bottom of the config under `SELECTIONS`.

**Presets**

`milk` functions similarly to `jarate` for the Sniper which we'll get to later. It'll make the script immediately switch to the primary (Scattergun) after throwing the milk. If you hold `ALT` while you throw the milk, you'll switch to your melee instead. It also enables the default crosshair for the milk and prevents the viewmodel from disappearing.

`pistol` is the default preset available and behaves like you would expect a hitscan weapon to behave in this config. It uses the small dot crosshair and hides the viewmodel when you fire it. Again, this can be changed by editing the part `alias vm_slt_2 vm_0` to `alias vm_slt_2 vm_1` in the `PISTOL` section. Like so:

```
//[ PISTOL
alias pistol "alias sw_milk_n;cc_pistol_n;alias cc_pistol_n;alias vm_slt_2 vm_1;alias xhair_2 exec xhair_precise"
alias cc_pistol_n cc_pistol
alias cc_pistol cc_emit #Pistol
//]
```

The disabled script is intended to be used with the pistol. What it's supposed to do is make `mouse2` (right-click) switch to your pistol and start attacking, but there are a lot exceptions that have to programmed, such as using the Sodapopper and the Sandman, and a more recent issue, I wrote the presets afterwards so currently there are a lot of names that overlap and that can't happen. That's why it's disabled. I also just don't like the script very much. I never used it and found that it more trouble than it was worth for me personally.

By default, these are the loadout presets:

| Loadout	| Preset	|
|:---------	|:--------- |
| A			| pistol	|
| B			| milk		|
| C			| milk		|
| D			| milk		|
| Default	| pistol	|

**Scout features in a table**

| Aliases				| Description |
|:---------------------	|:----------- |
| `milk`				| Will activate the Milk setting. Default crosshair. Switches to primary (Scattergun) after throwing. If holding `ALT`, switches to melee. |
| `pistol`				| Will activate the Pistol setting. Dot crosshair. Hides viewmodel when firing. |
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Soldier
Soldier is really straightforward. It's mostly stock settings with several loadout presets and a market garden script for the rocket launcher. `help_class` will list the loadout preset aliases. You can change what loadouts get what setting in the `PRESETS` section. You can see how to disable the automatic preset switching by using `help_loadout` (`loadoutpresets_1` and `loadoutpresets_0`). Even if you disable it, you should still put the preferred preset at the bottom of the config under `SELECTIONS`.

Of course, you can also edit the presets. For example, if you want to not hide the viewmodel when firing the shotgun, you can change the part `alias vm_slt_2 vm_0` to `alias vm_slt_2 vm_1`.

**Presets**

`shotgun` will make it so that on slot2 the crosshair is a dot, and the viewmodel will disappear when you shoot. This is the default preset, meaning that it's loaded on startup, and if you disable the automatic switching, this is the preset that will be used unless you switch it.

`banner` will make the crosshair the default one as opposed to the dot, and the viewmodel will not disappear when firing.

`gunboats` will remove slot2 from the mousewheel and any attempts to go to slot2 won't change any script settings like crosshair or viewmodel. This is also used for the Base Jumper and Mantreads, I just called it Gunboats because it's the most common of those items for the Soldier.

There is also support for linking the below script settings regarding rocket jumping to a loadout preset, but this is not something I do in my config. See below.

By default, these are the loadout presets:

| Loadout	| Preset	|
|:---------	|:--------- |
| A			| shotgun	|
| B			| gunboats	|
| C			| banner	|
| D			| gunboats	|
| Default	| shotgun	|

**Market Garden, Cow Mangler 5000, rocket jumping, and c-tap scripts**

With the market garden script, if you press `mouse2` (right-click) while having the rocket launcher out, you'll shoot and immediately pull out your melee (intended to be the Market Gardener). `mg_t` (toggles), `mg_1` (enables), `mg_0` (disables).

If you enable the rocket jump script, you'll automatically crouch, jump, and shoot when pressing `mouse2` (right-click). This will also work in conjunction with the Market Gardener script, so that you also pull out the melee. `rj_t` (toggles), `rj_1` (enables), `rj_0` (disables).

I also wrote a c-tap script inspired by [Aegis](https://www.youtube.com/user/AcesGamer "Aegis on YouTube"), in particular his video on [c-tapping](https://youtu.be/U-n7wcrVDMI "C-Tapping, for not-so dummies. JUMP: 1"). This script binds the crouch function to `mouse2` (right-click), so that c-tapping can be accomplished in an easier fashion by pressing `mouse2` and immediately pressing jump plus attack right after. A "one-two punch" as Aegis describes it. The c-tap script overwrites the Market Garden and rocket jump script. Turning the c-tap script off will restore whatever rocket jump scripts described above that you had active prior to activating the c-tap script. `ctap_t` (toggles), `ctap_1` (enables), `ctap_0` (disables).

On the less useful side, I also made a c-tap script tied to the `spacebar`. When engaged, the `spacebar` will also stop crouching, meaning that you can crouch normally, then hit `space` to stop crouching and immediately jump while also firing with `mouse1` to do a rocket jump. In theory this should result in a c-tap but in practice it rarely works properly, so I really don't recommend using it. It's toggled on and off by hitting `shift`.

Seeing as these scripts (except for the one bound to `space`) take up `mouse2` (right-click) which is used for `+attack2` when using the Cow Mangler 5000, I've made two settings for the Cow Mangler that can partially disable the scripts to allow for `mouse2` to trigger the charged shot. One of those settings for the Cow Mangler is called `cm_pres_noassist` which completely diesables all the jump assist scripts and allows `mouse2` (right-click) to be used to do the charge shot. `cm_pres_assist` keeps your active jump assists, but allows you to press `ALT + mouse2` to do the charge shot. To change the Cow Mangler preset setting navigate to the `SELECTIONS` section at bottom of the Soldier config and change the line `alias cm_pres cm_pres_assist` to `alias cm_pres cm_pres_noassist`. To activate said Cow Mangler setting: `cm_t` (toggles), `cm_1` (enables), `cm_0` (disables).

The Market Gardener script is enabled by default, and the rocket jump script is not, but all of this can be changed in the `SELECTIONS` section at the bottom of the class config. It can also be tied to a loadout preset, but this is not currently something I want in the config. How you'd do this is to add the aliases `mg_1n` or `mg_0n`, `rj_1n` or `rj_0n`, or `cm_1n` or `cm_0n` to the loadout aliases. Remember to add `""` around it when there are more than one thing tied to the loadout alias. If you have a specific loadout for the Cow Mangler, by all means put it in there.

Scripts like these that emulate or mimic movement that you're supposed to be doing naturally/manually usually come with some pretty serious downsides that I want to talk about briefly. The downside to the market garden script is that if you switch back to the Rocket Launcher and try to jump again by pressing `mouse2` to quickly after switching, it'll switch to the melee before it's actually fired a rocket, because you pressed it before you were able to even fire.

The downside to the rocket jump script is that it doesn't allow you to not crouch while jumping and you can't c-tap using that script, but it's useful for beginners. Although, I'd advise beginners to learn how to rocket jump the normal way.

In general, I'd advise you to rocket-jump and market garden the normal way, as relying on a script can leave you with some bad habits. For instance, always jumping with the melee out is a big disadvantage if you play TF2 slightly more seriously. It also makes you used to jumping with right-click as opposed to left-click which won't be the case if you're using the Cow Mangler 5000 with the `noassist` preset that disables all those jump assists, or if you're playing on other classes like the Pyro's Detonator jump.

**Offline rocket jump practice**

This is technically All-Class but it's most suited for rocket jumping. When you go on an offline private server (listenserver), it'll load up a bunch of coordinates for different maps and will activate the ones for the map your on. The command `tele` will teleport you to the active coordinates (referred to as *positions*). `tele` is bound to `mouse3` by default, but because it gets overridden by the autoexec and class config, you'll have to manually bind it (`bind mouse3 tele`) or manually re-execute the listenserver config (`exec listenserver`).

To change between the positions use the aliases `pos#` where `#` is a number designating the position starting from `1`. For example, practice `pos1` which is enabled by default, then when you're donw with that jump, put `pos2` and teleport to the next jump etc. This is most ideal for `pl_badwater` and `pl_upward`. Note that not all maps support very many jump positions.

**Soldier features in a table**

| Binds							| Description |
|:-----------------------------	|:----------- |
| `MOUSE2` - Rocket Launcher	| Uses whatever rocket jump assist script you currently have active (Market Garden and/or rocket jump, or c-tap). With Cow Mangler preset `noassist` will fire charged rocket like normal. |
| `ALT + MOUSE2` - Cow Mangler	| Fires charged rocket if using the Cow Mangler preset `assist`. This allows to also use rocket jump assists. |

| Aliases							| Description |
|:---------------------------------	|:----------- |
| `banner`							| Will activate the Banner setting. Default crosshair. Doesn't hide viewmodel when firing. |
| `gunboats`						| Will activate the Gunboats setting. Removes slot2 from rotation and neutralizes slot settings. |
| `shotgun`							| Will activate the Shotgun setting. Dot crosshair. Hides viewmodel when firing. |
| `rj` aliases (rocket jump)		| Rocket-jump script that automatically crouch-jumps and fires with `mouse2`. `rj_t` (toggles), `rj_1` (enables), `rj_0` (disables). |
| `mg` aliases (Market Gardener)	| Market Gardener script that automatically switches to your melee after jumping with `mouse2`. `mg_t` (toggles), `mg_1` (enables), `mg_0` (disables). |
| `cm` aliases (Cow Mangler)		| Cow Mangler setting that partially disables the above two scripts depending on the Cow Mangler preset and partially makes right-click alt-fire as it's supposed to depending on preset. `cm_t` (toggles), `cm_1` (enables), `cm_0` (disables). |
| `cm_pres` aliases (Cow Mangler presets)	| `cm_pres_assist` keeps your jump assist script and makes `ALT + MOUSE2` alt-fire. `cm_pres_noassist` disables jump assist scripts and makes `MOUSE2` alt-fire like normal. `alias cm_pres [PRESET]` to change it. |
| `loadoutpresets` aliases			| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Pyro
Pyro is also pretty simple. Dot crosshairs on primary (Flame Thrower) and secondary (Shotgun/Flare Gun), and default crosshair for melee. I also have a ding sound that plays to alert you when the Flare has fully reloaded. Note that this also plays for the shotgun, but you can disable it by changing the line `flare_ding_1` to `flare_ding_0` in the `SELECTIONS` section at the bottom of the config. I also tied them to different loadouts. You can change what loadouts get the setting enabled/disabled in the `PRESETS` section, and you can see how to disable the automatic preset switching by using `help_loadout` (`loadoutpresets_1` and `loadout_presets_0`).

On the derpier side, I also have a Panic Mode button that will cause you to spray flames like a maniac.

**Pyro features in a table**

| Binds					| Description |
|:---------------------	|:----------- |
| `SHIFT`				| Toggles Panic Mode! AAARRRGGHHHHH FIIIIIRREEEEEEE!!! |
| `ALT`					| Also disables Panic Mode. Only disables. |

| Aliases				| Description |
|:---------------------	|:----------- |
| `panicmode` aliases	| `panicmode_t` (toggles), `panicmode_1` (enables), `panicmode_0` (disables). |
| `flare_ding` aliases	| A ding sound to alert you when the Flare Gun is reloaded. `flare_ding_t` (toggles), `flare_ding_1` (enables) (default), `flare_ding_0` (disables). |
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Demoman
Demoman is almost a very basic config. He's basically all stock settings. He has a small dot crosshair on primary (grenade launcher) and secondary (Sticky Launcher), and the default crosshair for melee. Aside from that, he's all stock. Doesn't even hide his viewmodels. Nothing fancy at all.

The one thing that makes it complicated is the support added for removing certain weapon slots, like putting on a shield or boots to go demoknighting. This feature took a lot of extra behind-the-scenes coding to get to work properly, but that is also the only feature of the Demoman config that is remotely different from the others.

`help_class` will list the loadout preset aliases. You can change what loadouts get what setting in the `PRESETS` section. You can see how to disable the automatic preset switching by using `help_loadout` (`loadoutpresets_1` and `loadoutpresets_0`). Even if you disable it, you should still put the preferred preset at the bottom of the config under `SELECTIONS`.

**Presets**

`boots` is the preset for removing slot1. It takes it out of the mousewheel rotation and makes it so that nothing should ever activate the slot1 settings. This is for whenever you have the boots on, but not the shield. It is also used for equipping the Base Jumper without shield.

`shield` is the preset for removing slot2. It takes it out of the mousewheel rotation and makes it so that nothing should ever activate the slot2 settings. This is for whenever you the shield on, but not the boots.

`knight` is the preset for removing slot 1 *and* slot2. It takes them out of the mousewheel rotation and makes it so that nothing should ever activate those settings. This is for whenever you play as *full* demoknight and can only use the melee weapon. It is also used for for equipping the Base Jumper with the Shield.

`man` is the preset for the stock Demoman. No weapon slots are removed and everything functions as normal. This is the default preset.

The setting presets are also tied to loadout presets which, of course, you can edit to your pleasing. By default, these are the loadout presets:

| Loadout	| Preset	|
|:---------	|:--------- |
| A			| man		|
| B			| shield	|
| C			| knight	|
| D			| man		|
| Default	| man		|

**Demoman features in a table**

| Aliases					| Description |
|:-------------------------	|:----------- |
| `boots`					| Will activate the Boots setting. Removes slot1 from rotation and neutralizes slot settings. |
| `shield`					| Will activate the Shield setting. Removes slot2 from rotation and neutralizes slot settings. |
| `knight`					| Will activate the Demoknight setting. Removes slot1 and slot2 from rotation and neutralizes slot settings. |
| `man`						| Will activate the Demoman setting. Uses all weapon slots and activates slot settings. |
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Heavy
You might not think that heavy would be very complicated to script for, but you'd be surprised how much advanced stuff you have to account for when considering the Sandvich and other related food items.

As far as crosshairs, the primary (Minigun) uses a small dot crosshair, the secondary when using the `shotgun` preset also uses the small dot crosshair but uses the default crosshair with `sandvich` and `buffalo` presets, and the melee uses the default crosshair.

`help_class` will list the loadout preset aliases. You can change what loadouts get what setting in the `PRESETS` section. You can see how to disable the automatic preset switching by using `help_loadout` (`loadoutpresets_1` and `loadoutpresets_0`). Even if you disable it, you should still put the preferred preset at the bottom of the config under `SELECTIONS`.

**Presets**

`sandvich` is the preset for using the Sandvich. It uses the default crosshair and switches to your last active weapon when used/thrown in order to track your weapon switches. This is the default preset.

`buffalo` is the preset for using the Buffalo Steak Sandvich. It uses the default crosshair and switches to your melee weapon when used, and your last active weapon when thrown in order to track your weapon switches.

`shotgun` is the preset for using the Shotgun. It uses the small dot crosshair and hides viewmodel when firing.

| Loadout	| Preset	|
|:---------	|:--------- |
| A			| sandvich	|
| B			| shotgun	|
| C			| buffalo	|
| D			| sandvich	|
| Default	| sandvich	|

**Throw sandvich message**

If you have a food preset active (`sandvich` or `buffalo`), this script will alert your team in team chat to you throwing your sandvich. So when you throw it on the ground, it say "throwing sandvich" in team chat.

The aliases to enable/disable/toggle this script are `msg_food_tn` (toggles), `msg_food_t1` (enables), and `msg_food_t0` (disables).

**Heavy features in a table**

| Binds							| Description |
|:-----------------------------	|:----------- |
| `MOUSE2` - Food item			| Puts a message in chat letting your team know that you threw some food on the ground if `msg_food` is enabled. |

| Aliases					| Description |
|:-------------------------	|:----------- |
| `sandvich`				| Will activate the Sandvich setting. Default crosshair. Allows the possibility of `msg_food` and switches weapon to last equipped when food is used/thrown. |
| `buffalo`					| Will activate the Buffalo setting. Default crosshair. Allows the possibility of `msg_food` and switches weapon to melee when food is used Last equipped when thrown. |
| `shotgun`					| Will activate the Shotgun setting. Dot crosshair. Hides viewmodel when firing. Will not trigger `msg_food`. |
| `msg_food` aliases		| The chat message when throwing food. `msg_food_tn` (toggles), `msg_food_t1` (enables), `msg_food_t0` (disables). |
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Engineer
The Engineer is a fairly mechanically complex class, which means that it's the perfect candidate for some scripting fun. But first, the crosshairs. The primary (Shotgun) and secondary (Pistol) use the small dot crosshair and hide your viewmodel when firing. The melee uses the default crosshair.

**Presets**

I only have one preset setting for Engineer and that is the `gunslinger_1` (and `gunslinger_0` and `gunslinger_t`) which changes what weapon you switch to after building a building with the *quick-build* script (try saying that 5 times fast). This is described in more detail below. The `gunslinger` preset is enabled on the last loadout preset (D).

There's also a setting for a *Eureka Effect teleport* script but I don't use a loadout preset to toggle it (it's just enabled by default, see more details below), but it is totally possible to add this setting to a loadout preset if you don't want it enabled all the time.

**Quick-build**

The `F1 - F4` keys are designed to allow you to build buildings in fewer button presses and also bypassing the PDA menus. What happens is that, 1. you use the commands directly, 2. you destroy the existing building before pulling out the replacement. This means that, before, if you were to destroy an existing sentry and build a replacement, you'd press `5, 1, 4, 1, mouse1`. Now you only press `F1, mouse1`.

Holding `ALT` while picking a building (`ALT + F1 - F4`) will not build a new building, but will instead only destroy it. Interestingly enough, `ALT + F4` is completely safe! At least it is for me. Your mileage may vary, and I'm not responsible for any damage caused by exiting the game, physical, mental, or virtual.

When you place the building it will switch to the Wrench after building, but if you hold `ALT` while placing it with `mouse1` (left-click), it will instead switch to the Shotgun when releasing the mouse button. This can be edited if you so desire, but it's very deep in the code so don't try it if you don't know what you're doing. It's in the `qb_norml` alias.

Because this feature is most handy when using the Gunslinger for pulling out the Frontier Justice after placing a mini-sentry, I also made a `gunslinger` setting that reverses the weapons it pulls out, so that by default it pulls out the Shotgun after placing a *sentry* (not the other buildings), but if you hold `ALT` it will pull out for Wrench after placing the sentry (again, the other buildings behave as normal). `gunslinger_t` (toggles), `gunslinger_1` (enables), `gunslinger_0` (disables).

Known minor, unfixable bug: Attack-cancelling out of a the Build PDA will attack with whatever weapon you had out but will think you have the Wrench.

**Auto-wrench**

Simple. If you hold `ALT` while pressing `mouse1` (left-click) to attack while having the wrench as your active weapon, then you'll continue attacking even after releasing the mouse button. This is useful for times when you know that you only have to wrench your buildings for a little while, like setup time or Mann vs. Machine (MvM). Left-click again or switch to a weapon (including to the wrench) to stop attacking.

**Eureka teleport**

If you enable a setting called `eureka_1` then hitting `B` will teleport you to your spawn using the Eureka Effect. Holding `SHIFT` while pressing `B` (`SHIFT + B`) will teleport you to your teleporter exit instead. This setting is enabled by default so you don't have to worry about enabling the setting whenever you wish to use the Eureka Effect. I only made it into an on/off setting to give the option to disable it if you don't want to accidentally hit `B` and switch to your wrench for no reason. `eureka_0` to disable. `eureka_t` to toggle it.

Credit goes to [Uncle Dane](https://www.youtube.com/user/danethebrain "Uncle Dane on YouTube") or whoever made it for him. I got the script from [this video](https://youtu.be/4ABLluYwt9Q "The Jag Effect Rollout") he made.

**Engineer features in a table**

| Binds					| Description |
|:---------------------	|:----------- |
| `B`					| With Eureka Effect will teleport to spawn. |
| `SHIFT + B`			| With Eureka Effect will teleport to teleporter exit. |
| `F1 - F4`				| Quick-build. Destroys and builds the corresponding buildings. In order; Sentry, Dispenser, Entrance, Exit. Brings out wrench by default when building (Shotgun when holding `ALT`. Reversed with `gunslinger_1`). |
| `ALT + F1 - F4`		| Will destroy corresponding buildings instead of building. Funnily enough, `ALT + F4` does not quit the game. At least mine doesn't. You mileage may vary. |
| `F8`					| Player ready up in MvM and MM. |
| `ALT + MOUSE1` - wrench	| Auto-wrench. Keeps swinging. Press attack or a weapon equip to stop. |

| Aliases				| Description |
|:---------------------	|:----------- |
| `gunslinger` aliases	| Changes the `gunslinger_t` (toggles), `gunslinger_1` (enables), `gunslinger_0` (disables). |
| `eureka` aliases		| Enables/disables `B` and `ALT + B` teleporting using the Eureka Effect. Can be disabled because it switches to wrench when used. `eureka_t` (toggles), `eureka_1` (enables) (default), `eureka_0` (disables). |
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Medic
Medic is pretty complicated and has a lot of features. But first, the crosshairs. The primary (Syringe Gun/Crossbow) and the melee (Bonesaw) use the small dot crosshair, and the secondary (Medigun) uses the default crosshair to get that awesome medic cross crosshair.

`help_class` will list some of the commands for the different settings. A lot of the settings are enabled by default at the bottom of the file. If you wish to have certain settings disabled by default, feel free to change that at the bottom of the file in the `SELECTIONS` section. Just try changing the `1`s to `0`s.

**Presets**

Very simple. The last loadout slot activates the *Vaccinator* script. All the other loadouts turn it off. Se more details on the *Vaccinator scripts* further down.

See how to disable automatic setting switches when using the `KEYPAD` to change loadouts by putting `help_loadout` in console (`loadoutpresets_1` and `loadoutpresets_0`). Even if you disable it, you should still put the preferred preset at the bottom of the config under `SELECTIONS`. Most likely `vacc_t0` unless you *really* like the Vaccinator.

**Inverted Medigun/Autoheal**

I use an autoheal script that automatically latches on to people with the medigun. It's a simple trick, it just always attacks. To stop attacking (and switch heal target) press/hold `mouse1` (left-click)

The commands to toggle this on/off are `invmed_t1` and `invmed_t0` respectively. `invmed_tn` toggles it.

**Pop**

When you press `mouse2` (right-click) with any weapon, you will switch to the medigun, attempt to pop Über, and say in team chat "~ ~ FRIENDLY UBER POPPED ~ ~". You have to hold `mouse2` for about a second while switching weapons for it to properly pop the Über, but it works instantaneously when you're already on the Medigun.

The message in team chat can be turned on/off with the commands `pop_1` and `pop_0`. `pop_t` toggles it. Turning it off is most commonly used if you use the Quick-Fix or Vaccinator (the Vaccinator script also turns this off) and the pop is therefore not as big of a deal.

**Needle/Arrow**

If you hold `ALT` while attacking with `mouse1` (left-click) while using the primary or melee, you will switch to the Medigun as soon as you stop attacking, meaning that if you tap it, you'll switch almost instantly. For melee you have to hold the `mouse1` (left-click) all the way through the swing.

This script is meant to be used with the Crusader's Crossbow. You tap once to fire an a needle/arrow, and then immediately switch to the Medigun to continue healing.

It can be turned on/off/toggled with `ndl_1`, `ndl_0`, and `ndl_t`.

**Melee taunt**

Simple. If you hold `ALT` while pressing `mouse2` (right-click) while holding the melee weapon, instead of switching to the Medigun and popping Über (from the Pop script), you'll use the weapon taunt for the melee weapon. This is meant to mimic behaviour added into the game to make is easier to use the Amputator and Ubersaw taunts.

**Radar**

If you press `SHIFT` it should *ping* everyone on your team through walls to help you locate them, like sonar! It's a bit janky and might take a few tries to actually activate. It's also disabled in competitive matchmaking, I believe.

This script is also where you designate what you want your `hud_medicautocallersthreshold` at (the percentage health where your teammates' health will *ping* that they need healing). This is easy to change if you want to designate it in, say, `autoexec.cfg`, but there's really no point in doing that.

How you would designate it elsewhere in the config is to change the line `alias -radar hud_medicautocallersthreshold 75` to something like `alias -radar medcall_def`, and then put `alias medcall_def hud_medicautocallersthreshold 75` (or whatever value you want) anywhere in the config as long as it's before the line `-shift_n` found in `medic.cfg`. Alternatively, move `-shift_n` down to the bottom of the file.

**Team calls**

Pressing `F1` will fake an Übercharge callout. Basically, you'll say the voice command for having just gained Über to mislead the enemy. This is rarely if ever used. The exact message is "~ ~ Uber faked.. ~ ~". You can turn the message on/off/toggle with `fake_1`, `fake_0`, and `fake_t`.

Pressing `F2` will mask your actual Über callout so that the enemy won't know that you just got Über. This is more commonly used but I still never use it. It also announces in team chat that you now have a full Übercharge. The exact message is "~ ~ Uber ready! ~ ~". You can turn the message on/off/toggle with `mask_1`, `mask_0`, and `mask_t`.

Holding `ALT` and pressing `E` will announce in team chat that you're interested in popping the Über. This replaces the script that will ask for an Über to be popped on you (because you're the popper now). The exact message is "I'm about to give you Uber. Get ready!"

You can add more chat lines for the sake of variety and even randomize for line is used by tying it to the `WASD` keys, but this is currently not in the config. It is possible, though, and not that hard to write considering I've done most of the ground work for this type of script. The reason it's currently not a thing is because there's no practical reason to have more lines. It would for just be to add more flavour.

**Crossbow ding**

Basically, it makes a *ding* sound when the crossbow is fully reloaded after firing. This persists through weapon change, so if you fire an arrow and switch to the Medigun (maybe through the Needle/Arrow script), then it will still make the *ding* sound when the crossbow has reloaded passively. Keep in mind that this is based on you attacking/pressing `mouse1` (left-click) while having the primary out, so if you spam-click, it will spam-ding!

You can turn the *ding* sound on/off/toggle with `crossbow_ding_1`, `crossbow_ding_0`, `crossbow_ding_t`.

**Vaccinator**

This is a script for switching resistances using the thumb buttons on the mouse. It only really works if you have a mouse with 3 thumb buttons. Basically, when you hold `ALT` and press the thumb buttons on the mouse, it will switch to a different resistance. You have to press it until it reaches that state, and from that point pressing it will no longer advance the resistance. `mouse5` is bullet resistance, `'` (apostrophe) aka `mb_6` aka the "Snipe button" (which is the extra button that doesn't exist on many mice) is explosive resistance, and finally `mouse4` is fire resistance.

`vacc_tn` toggles Vaccinator script on/off, `vacc_t1` enables it, and `vacc_t0` disables it. These are also controlled by the loadout presets, so that Vaccinator is only enabled on the last loadout slot (D). Feel free to change this if you need to on a different loadout. You can also see how to disable the loadout specific settings by putting `help_loadout` in console (`loadoutpresets_1` and `loadoutpresets_0`). Even if you disable it, you should still put the preferred preset at the bottom of the config under `SELECTIONS`. Most likely `vacc_t0` unless you *really* like the Vaccinator.

**Medic features in a table**

| Binds					| Description |
|:---------------------	|:----------- |
| `F1`					| Über Fake to mislead the enemy team. Message can be toggled on/off with `fake_1`, `fake_0`, and `fake_t`. |
| `F2`					| Über Mask to hide information from the enemy team. Message can be toggled on/off with `mask_1`, `mask_0`, and `mask_t`. |
| `MOUSE2` - any weapon	| Switches to Medigun, pops Über, and alerts your team. Message can be toggled on/off with `pop_1`, `pop_0`, and `pop_t`. |
| `ALT + MOUSE1` - primary + melee | Switches to Medigun after firing. Tap for instant switch. Used for crossbow. Can be toggled on/off with `ndl_1`, `ndl_0`, and `ndl_t`. |
| `ALT + MOUSE2` - melee	| Uses melee weapon taunt. |
| `ALT + E`				| Alerts your heal target in team chat that you want to pop Über. |
| `ALT + THUMB BUTTONS`	| When Vaccinator is enabled, these will switch to different resistances when pressed multiple times. |
| `KEYPAD 0`			| Resets the Vaccinator script back to the Bullet resistance state. Switch to the bullet resistance, then press the reset to re-sync the script. |
| `SHIFT`				| Radar script to locate teammates through walls. Disabled in matchmaking. |

| Aliases				| Description |
|:---------------------	|:----------- |
| `fake` aliases		| `fake_t` (toggles), `fake_1` (enables) (default), `fake_0` (disables). |
| `mask` aliases		| `mask_t` (toggles), `mask_1` (enables) (default), `mask_0` (disables). |
| `vacc` aliases		| `vacc_tn` (toggles), `vacc_t1` (enables), `vacc_t0` (disables) (default). |
| `crossbow_ding` aliases	| A ding sound to alert you when the Crossbow is reloaded. `crossbow_ding_t` (toggles), `crossbow_ding_1` (enables) (default), `crossbow_ding_0` (disables). |
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Sniper
Sniper is similar to Soldier in that it's mostly stock settings with presets. `help_class` will list the loadout preset aliases and the aliases required for changing the *XTRA ZOOM* script. You can change what loadouts get what setting in the `PRESETS` section. You can see how to disable the automatic preset switching by using `help_loadout` (`loadoutpresets_1` and `loadoutpresets_0`). Even if you disable it, you should still put the preferred preset at the bottom of the config under `SELECTIONS`.

The Sniper config is also intended to have different settings for different ways to control the Classic sniper rifle. I used to have that programmed in an older version of my config but I never got around to porting it into the newer config. Maybe some day.

**Presets**

`jarate` is the preset for using Jarate. It will use the default crosshair and will switch to your melee immediately after throwing Jarate. If you hold `ALT`, it will switch to your primary (Sniper Rifle) instead. The switching can be reversed by editing the `+jarate_t` and `-jarate_t` aliases. This setting is enabled by default.

`razorback` is pretty much identical to Gunboats. It will remove slot2 from the mousewheel and any attempts to go to slot2 won't change any script settings like crosshair or viewmodel.

`smg` is the preset for using the SMGs for Sniper. It's the equivalent of Soldier's Shotgun preset. It will use the dot crosshair and will hide the viewmodel when firing.

By default, these are the loadout presets:

| Loadout	| Preset	|
|:---------	|:--------- |
| A			| jarate	|
| B			| razor		|
| C			| smg		|
| D			| smg		|
| Default	| jarate	|

**XTRA ZOOM**

*XTRA ZOOM* will half your scoped sensitivity whenever you want more precise aim for long-range shots. It comes with two presets, but I recommend using the one enabled by default.

`help_class` will show the aliases required to change this script. They are `xtra_zoom_pres`, `xtra_zoom_pres_+`, and `xtra_zoom_pres_t`. `xtra_zoom_pres` is the neutral alias and `xtra_zoom_pres_+` and `xtra_zoom_pres_t` are the actual presets.

`xtra_zoom_pres_+` is the preset where *holding down* `SHIFT` will half the zoom sensitivity making it more precise. This is the preset enabled by default.

`xtra_zoom_pres_t` is the preset where `SHIFT` acts as a *toggle* so pressing it once will half the zoom sensitivity and pressing it again will restore it to the default. This doesn't work well at all in my opinion, but it's there as an option. Currently there's no reset for it, so you'll have to keep track of whether or not the sensitivity is halfed yourself.

To change presets either change the line `alias xtra_zoom_pres xtra_zoom_pres_+` to the desired preset, or type it in console followed by `xtra_zoom_pres`. Note that this won't save between sessions.

**Sniper features in a table**

| Binds					| Description |
|:---------------------	|:----------- |
| `SHIFT`				| The toggle for *XTRA ZOOM*. Will half the scoped sensitivity when engaged. |

| Aliases				| Description |
|:---------------------	|:----------- |
| `jarate`				| Will activate the Jarate setting. Default crosshair. Switches to melee after throwing. If holding `ALT`, switches to primary (Sniper Rifle). |
| `razorback`			| Will activate the Razorback setting. Removes slot2 from rotation and neutralizes slot settings. |
| `smg`					| Will activate the SMG setting. Dot crosshair. Hides viewmodel when firing. |
| `loadoutpresets` aliases	| Automatically switching settings when using the `KEYPAD` to switch loadout. `loadoutpresets_t` (toggles), `loadoutpresets_1` (enables) (default), `loadoutpresets_0` (disables), `alias loadoutpresets_n loadoutpresets_0` to disable globally. |

##[^](#top "Back to Top")Spy
Welcome to my world. This is the crown jewel of the config and one of the most complicated class configs along with Engineer and Medic, so it's going to take a while to go through everything. First up is the crosshairs. The primary (Revolver) as well as the melee (Knife) use the small dot crosshair, and the secondary (Sapper) uses the default crosshair which in the case of the Sapper looks like a small bracket square thing. I like it.

There are no loadout preset settings, and putting together a `help_class` is going to take a while, so I've put it off for now.

**Quick-Disguise**

I have binds to quickly use the disguise commands without having to go into the disguise menu. These are mapped to the `F#` keys, so `F1 - F9` for the default disguise menu (as opposed to *concise*) with each key corresponding to each class. Holding `T` will toggle the keys to disguise as the corresponding *friendly* class. As I hinted above, I also made a *concise* quick-disguise script. This makes it behave like the concise disguise menu, where `F1` activates the first three classes, `F2` the next three, and `F3` the last three. After activating the desired batch, you hit `F1 - F3` to disguise as that class in the selected bunch, so to give some examples:

`F1 + F1` = Scout

`F1 + F3` = Pyro

`F2 + F3` = Engineer

`F3 + F2` = Sniper.

To reset the script back to the beginning, say if you hit the wrong button and selected the wrong batch of three, just hit `F4`. This will reset it and you can then select a different batch.

I also have a *random disguise* button bound to `F` that applies a random disguise with normal-ish move speed (Demoman being the slowest). It's cycled using the `WASD` keys. There's a also a loop that can cycle it, but that just lowers your framerate for almost no reason, so I have it disabled. Hold `ALT` while pressing the `F` key to disguise as a random *friendly* disguise excluding the Demoman because it has lower move speed. So `ALT + F` in total.

Because these scripts takes up a lot of the `F#` keys, the actual `F` key, and also `T`, some functions have had to be rebound elsewhere.

`O` is now the `inspect` button instead `F`

`P` is now the spray button instead of `T`.

`]` os now the ready up button instead of `F4`.

`F10` is now the replay button instead of `F6`.

`F12` is now the screenshot button (in the form of JPEG) instead of `F5`.

There is sadly no rebind for the "Report Player" button, the "Ready Up" button but the command is `player_ready_toggle` in case you need to use it. Also no rebind for the "Quit" button but who even uses that thing? Also apparently there's a bind for "Replay Tips", this is not rebound because why does it even exist.

I'll try and squeeze in those missing binds, at least for the "Ready Up" button.


**Disguise weapon**

Holding `ALT` and pressing `thumb buttons` will change your disguise weapon corresponding to the button you pressed. Like I've said before, I have three thumb buttons on my mouse, so I can have each button correspond to a specific designated weapon, but for the public release of the config I'll enable a preset designed for two buttons called `dwep_pres_othr`. What this does is ensure that you can switch to all weapons no matter what weapon you currently have out, *but* it is somewhat complicated. The thumb buttons correspond to the weapons that you *don't* currently have out, and to switch disguise weapon to your currently equipped weapon, you'd hit `B`. See the table below.

| 										| Equipped Weapon 1	| Equipped Weapon 2		| Equipped Weapon 3 |
|:-------------------------------------	|:-----------------	|:---------------------	|:-----------------	|
| **`B`**								| Disguise Weapon 1	| Disguise Weapon 2		| Disguise Weapon 3 |
| **`MOUSE5` (top thumb button)**		| Disguise Weapon 2	| Disguise Weapon 1		| Disguise Weapon 1 |
| **`MOUSE4` (bottom thumb button)**	| Disguise Weapon 3	| Disguise Weapon 3		| Disguise Weapon 2 |

This script relies on the release of the button to bring you back to your current weapon, but because it happens so quickly, sometimes something goes wrong and it might not actually switch your disguise weapon properly. You shouldn't end up with a different *actual* weapon, but the disguise weapon might not be what you wnated all the time, so in those cases, you'd have to press the button multiple times to get the desired disguise weapon. To combat this I've also written a version that instead relies on `wait` to make sure that all commands happen in the right order at a set pace as opposed to tying it to you releasing the button. The problem is that `wait` is inherently unreliable at timing since it's tied to your own framerate. Because of this I've disabled the `wait` version by default, but you can enable it in the config. The exact timing values depend on your framerate, and if the timing is off and you press the button too quickly, then you could end up with the wrong weapon equipped which is way worse than just the wrong disguise weapon.

Back to the config features! If you hold `ALT` while using the `mousewheel` it will also change the disguise weapon alongside your own weapon. It also makes the mousewheel cycle around at 1 and 3, i.e. when you scroll down on 3, it goes to 1, and when you scroll up at 1, it goes to 3. This is not the normal behaviour. Use this to make your disguise more believable by changing weapons a lot more than other spies would. OIr not, it's kind of impractical to do because you can't attack at all and might even lose track of what weapon you have out, but it's kind of cool, and it's fun using this to mess with people at the setup gate.

The weapon spam loop which is a feature for all classes will in the case of the Spy also change the disguise weapon. This makes for even more fun at the setup gate.. because spamming your weapons that fast is silly.. that's why. To reiterate, the loop is bound to `KEYPAD 3`. When `wait` is disabled, instead of engaging a loop, it'll change the mousewheel to switch weapons much like it's described above except that you don't need to hold `ALT`.

**Amby snipe**

By pressing `SHIFT` while holding the primary (Revolver), it will hide the viewmodel, lower your sensitivity and FOV (Field of Vision) which acts as a Sniper-esque scoped zoom. This is most useful with the Ambassador. Press `SHIFT` again, `ALT`, `mouse2`(right-click) to cloak, or hit any weapon switch including the primary again will turn the snipe zoom off. Toggling it off using `SHIFT` will still have the viewmodel off to let you continue shooting without the viewmodel.

**Voice masking (Sapper and Watch)**

If you hold `ALT` while attacking with the Sapper or while hitting `mouse2`(right-click) to cloak, it will use a voice line to try and mask the sound of what you're actually doing. This could be the sound of decloaking or the enemy Engie shouting "Spah is sappin' mah Sentry!"

This is not a very important script but it's kind of useful sometimes, I guess. I never really use it, though.

Currently it just cycles the voice lines in a set order, but it could easily be more randomized by tying the cycle to the `WASD` keys. This, however, adds another alias frequently being executed that has almost no effect because the feature is rarely used. So I've omitted that part, even if it doesn't affect performance in any tangible way, there's just not enough of a practical purpose to warrant it.

**Sapping message**

Whenever you attack with the sapper out, it'll put "sapping" in team chat to let your team know that you probably just sapped something, and maybe they should push in.

You can toggle this, and turn it on/off with the commands `sapping_t`, `sapping_1`, and `sapping_0`.

**Automatic re-disguise**

If you attack with the knife while holding `ALT` (`ALT + mouse1` in total), it will automatically use `lastdisguise` immediately after attacking. Effectively, you automatically re-disguise after stabbing a dude if you hold `ALT` while doing it.

You could easily make it so that this always happens, but automatically disguising can really mess you up if the disguise hits right before you cloak because the smoke trail will follow you through the cloak. That's why I use `ALT` as a modifier instead of having it be automatic all the time.

**Fake reload**

Similar to how attacking with a hitscan weapon will hide the viewmodel, and holding `ALT` while attacking will negate this feature, holding `ALT` while shooting the Revolver will also remove Auto-Reload leaving you with a bullet gone so that you can manually reload at any time. Switching weapons including to the Revolver will re-enable Auto-Reload.

This is useful for making your disguise more believable because your disguise will reload as you reload. The gist is that you shoot once, leaving you with a bullet missing, reload, and as you're about to finish the reload, quickly switch to a different weapon to stop the reload from finishing. This lets you repeat the fake reload ad infinitum.

I've also made a script for switching to a different weapon and back really quickly, so if you hold `ALT` while pressing `Q`, instead of only switching to your last used weapon, it will also switch back when you release `Q`. Basically, `ALT + Q` switches your weapon and back and does not re-enable Auto-Reload to let you keep reloading at will. This script is also useful for spam-equipping the Knife to hear/see that sweet, sweet balisong flipping.

All in all, this is the order of operations to do a fake reload:

| Step	| Key				| Description |
|:-----	|:-----------------	|:----------- |
| 1.	| `ALT + MOUSE1`	| Removes Auto-Reload and shows viewmodel. |
| 2.	| `R`				| Starts the reload animation. |
| 3.	| `ALT + Q`			| Cancels reload, switches to last weapon and back. |
| 4.	| ???				| Repeat steps 2-3 ad infinitum. |

**Revolver flash**

When you shoot the Revolver, it will change the crosshair to a much smaller dot. This is to combat the expanding crosshair that comes with shooting the Ambassador. You can toggle and turn on/off with the commands `xhair_flash_t`, `xhair_flash_1`, and `xhair_flash_0`.

**Revolver ding**

This is to alert you to the exact moment that the spread of the Revolver has been reset. For the Ambassador this is 0.95 sec. For every other Revolver it's 1.25 sec. Keep in mind that it's solely based on you pressing `mouse1` (left-click) to shoot, so if you spam-click, it will spam-ding! It's also only useful if you only want to shoot 100% accurate shots which is a huge handicap to your damage output. For this reason I've disabled this script by default.

To change between using the Ambassador timing or the Revolver timing, navigate to the `SELECTIONS` scetion at the bottom of the Spy config and change the line `alias sht_ding_pres sht_ding_amby` to `alias sht_ding_pres sht_ding_revo` (or the other way around if you have the other one active). This changes the timing when the script is active (`sht_ding_1`). The Ambassador timing is the default value.

To toggle the script, and turn it on/off use the commands `sht_ding_t`, `sht_ding_1`, and `sht_ding_0`.

**Spy features in a table**

| Binds					| Description |
|:---------------------	|:----------- |
| `F1 - F9`				| Quick-disguise. `T` hold-toggles to friendly disguises. `F1 - F4` in concise disguise mode. |
| `T + F1 - F9`			| Friendly quick-disguise. `F1 - F4` in concise disguise mode. |
| `F10`					| Save replay. `F6` is taken by the quick-disguise script. Could still have been bound in the concise version, but I decided against it for the sake of consistency. |
| `F12`					| Screenshot with JPEG. `F5` is taken by the quick-disguise script. Could still have been bound in the concise version, but I decided against it for the sake of consistency. This might take two screenshots depending on your Steam bind for that. |
| `MOUSE3` (middle mouse)	| Un-disguises you without attacking. Removes your disguise. |
| `F`					| Uses a random enemy disguise with normal-ish walk speed. Slowest is Demoman. `T` hold-toggles to friendly disguises. |
| `ALT + F`				| Uses a random friendly disguise with normal walk speed. Demoman is excluded. |
| `O`					| The inspect bind since `F` is taken up by the more useful random disguise bind. |
| `P`					| Spray. Rebound because `T` is taken up by the quick-disguise script. |
| `]`					| Ready Up! Rebound because `F4` is taken up by the quick-disguise script. |
| `SHIFT`				| Amby snipe. Lowers sensitivity and FOV to simulate a sniper scope. |
| `ALT + MOUSE1` - Revolver	| Doesn't hide viewmodel. Removes Auto-Reload to allow fake reloading. |
| `ALT + MOUSE1` - Sapper	| Uses a voice line when sapping to mask the enemy Engie's voice line calling out spy. |
| `ALT + MOUSE1` - Knife	| Automatically re-disguises as last disguise when attacking with the Knife.
| `ALT + Q`				| Switches to last weapon and back. Helps with fake reloading and spamming the Knife's draw animation. |
| `ALT + MOUSE2`		| Uses a voice line to mask the sound of the decloak. |
| `ALT + THUMB BUTTONS`	| Changes disguised weapon. Depends on the preset. |
| `ALT + MOUSEWHEEL`	| Makes the mousewheel switch the disguise weapon alongside your own weapon. Also makes the mousehweel cycle loop back around from 3 to 1 etc. |
| `KEYPAD 3`			| Engages the weapon spam loop (mousewheel when `wait` is disabled). For Spy this also changes disguise weapon. |


| Aliases				| Description |
|:---------------------	|:----------- |
| `disg_default`		| Activates the default quick-disguise script going from `F1 - F9`. As opposed to the concise disguise script. |
| `disg_concise`		| Activates the concise quick-disguise script going from `F1 - F4`. As opposed to the default disguise script. |
| `sapping` aliases		| Calls out "sapping" in chat when sapping. `sapping_t` (toggles), `sapping_1` (enables) (default), `sapping_0` (disables). |
| `xhair_flash` aliases	| Reduces size of Revolver crosshair when shooting. `xhair_flash_t` (toggles), `xhair_flash_1` (enables) (default), `xhair_flash_0` (disables). |
| `sht_ding` aliases	| A ding sound to alert you when the accuracy has reset to 100%. `sht_ding_t` (toggles), `sht_ding_1` (enables), `sht_ding_0` (disables) (default). |
| `sht_ding_pres` alias (timing presets)	| `sht_ding_amby` timing of 0.95 sec (default). `sht_ding_revo` timing of 1.25 sec. `alias sht_ding_pres [PRESET]` to change. |

#[^](#top "Back to Top")Close Captions
The initial Close Captions were created by **Clovervidia** and edited by me. That includes all the ones alerting about current events around you, like an Über being popped or a Scout catching fire etc. Most of the voice lines that are set to not say anything were also found by Clovervidia but I continued to support this, updating it as I find more voice lines that need to be taken care of.

All the script-specific captions, like alerting you when engaging certain presets, were made by me.

To enable them, put this in your `autoexec.cfg`. This is of course already there if you use my config.

```
closecaption	1
cc_subtitles	1
cc_lang			biscotti
```

If you want more thorough captions set `cc_subtitles 0`.

If the formatting on the captions look weird or aren't parsing correctly, it's probably because your caption field on the HUD is too narrow. If you use [my HUD (biscottiHUD)](http://www.teamfortress.tv/32405/biscottihud "biscottiHUD on teamfortress.tv"), then this won't be an issue seeing as it's the HUD that I used while making the captions. See more details on how to edit the caption field on the HUD in the guide by Clovervidia below.

I try to keep these updated so it doesn't flood your console with `Caption not found`.

[Here](https://steamcommunity.com/sharedfiles/filedetails/?id=167785751 "Clovervidia's Guide to CC") is a guide by **Clovervidia** that explains CC and how to use it.

#[^](#top "Back to Top")Credits
Thanks to [r/tf2scripts](https://www.reddit.com/r/Tf2Scripts "r/tf2scripts on Reddit") and [r/tf2scripthelp](https://www.reddit.com/r/tf2scripthelp "r/tf2scripthelp on Reddit") for being awesome and for occasionally teaching me some new tricks and helping me improve!

Thanks to Clovervidia for making the original captions.

#[^](#top "Back to Top")See it in action! YouTube!
I also have a [YouTube channel](https://www.youtube.com/user/SuperKavv "Medico di Biscotti on YouTube") that serves as a dump-site for the terrible, terrible videos I make from time to time. I use my own scripts for obvious reasons, and while I don't showcase the individual parts of my config, any video I make, any game of TF2 I play, is using this config.
