# Flatcore
A plugin for implementing all the various things necessary for flatcore

## Functionality
* Whenever a player spawns (either for first time, or after a death), they're placed in a random location (configurable)
* Beds only skip night - they don't have anything to do with respawning
* When a player dies, their entire inventory is destroyed (configurable)
* When a player dies, they are death-banned for 12h (configurable)
* When a player dies, custom messages are sent to the player, other players, and the console informing them about how their died
* When a player tries to join when death-banned, they will be rejected and told how long until they can rejoin
* For 30s after respawn (configurable), players have immortality - they cannot be damaged in any way, and mobs will not target them
* When a mob dies, if it wasn't killed by a player, it doesn't drop any loot
* Players, mods, and admins all have different death-ban times (admins cannot be death-banned)
* Players can read the weekly challenges in-game (both previous and current challenges)
* Mods can set the weekly challenges in-game (both previous and current challenges)
* The entire state of the plugin saves itself across /reloads, so /reloads are invisible to users
* Console can use all the commands
* Plugin configuration can be reloaded with a command

## Commands
* `/flathelp [page]` - lists all the "flatcore plugin" commands you have access to, and what they do
* `/challenge [id]` - tells you what the current weekly challenge is if you omit the [id], or tells you the weekly challenge for your specified id
* `/deathban <player> <time>` - set's a player's deathban. If they're not currently death-banned, it will death-ban them for a given time. Time in XwXdXhXmXs format
* `/startchallenge [id]` - starts you writing a weekly challenge ([id] is optional, if excluded a new challenge will be inserted). All chat you send to the server after sending this command will be appended to the challenge
* `/appendchallenge <text>` - explicitely adds text to the currently edited challenge (implemented for console use)
* `/stopchallenge` - stops writing a weekly challenge. All the chat text you've been accumulating in the challenge thing gets collected, and inserted as either an edited or new weekly challenge based on what ID you were editing
* `/flatreload` - reloads the flatcore config file

## Permissions
* flatcore.admin - cannot be deathbanned
* flatcore.mod - has a modified deathban time
* flatcore.help - can use the `/flathelp` command
* flatcore.challenge - can use the `/challenge` command
* flatcore.setchallenge - can use the `/startchallenge`, `/appendchallenge`, and `/stopchallenge` commands
* flatcore.deathban - can use the `/deathban` command
* flatcore.reload - can use the `/flatreload` command

## Config
	# define the center of spawn
	spawn-center-x: 0
	spawn-center-z: 0
	# define the spawn radius (in a square)
	spawn-radius: 10000
	# prevent pvp?
	disable-pvp: true
	# does the player's inventory get destroyed when they die?
	lose-inventory-on-death: true
	# how long normal players are death-banned for. Time in XwXdXhXmXs format
	death-ban-time: 12h
	# how long mods are death-banned for. Time in XwXdXhXmXs format
	mod-death-ban-time: 5m
	# should lightning strike where a player dies?
	thunder-death: true
	# should the server be made aware of their failure?
	broadcast-death: true
	# What to say to the person who dies
	private-death-message: "&4You've been killed by #deathreason &4and are now death-banned for &9#deathbantime&4. We'll see you then!"
	# What to say when someone tries to join the server but is still deathbanned
	deathban-message: "Sorry, #deathreason killed you and you're still banned for #deathbantime"
	# How long players are immortal for after spawning. Time in XwXdXhXmXs format
	spawn-immortality-time: 30s
	# How often to remind players of how much immortality they have left. Time in XwXdXhXmXs format
	spawn-immortality-reminder: 5s
	# The message that gets sent to a player when they're immortal
	spawn-immortality-message: "&aYou're immortal for #immortaltime!"
	# The message the gets sent to a player when they become mortal
	spawn-mortality-message: "&cYou''re no longer immortal! Good Luck!"
	# the various death messages, a random one from each list will be picked when a player dies
	# Must contain at least 1 line. If there are more, it will appear randomly when a person dies.
	# %n for player who died
	# %a name of player who attacked in pvp deaths
	# %i for item a player was using to kill someone else
	death-messages:
	  block-explosion:
		- "Careful &5%n&7, TNT goes boom!"
		- "&5%n&7 was last seen playing with dynamite."
		- "&5%n&7 exploded into a million pieces!"
		- "&5%n&7 cut the wrong wire!"
		- "&5%n&7 left his (bloody) mark on the world."
		- "&5%n&7 attempted to exterminate gophers with dynamite!"
		- "&5%n&7 played land mine hop scotch!"
		- "&5%n&7 stuck his head in a microwave!"
	  entity-explosion:
		- "Well... something exploded on &5%n&7!"
	  cavespider:
		- "&5%n&7 will never sing itsybitsyspider again"
		- "&5%n&7 is all webbed up."
		- "&5%n&7 was trampled by arachnids!"
		- "&5%n&7 was jumped by a spidah!"
		- "Spiders just climbed all over &5%n&7!"
		- "&5%n&7 forgot spiders could climb!"
	  contact:
		- "&5%n&7 got a little too close to a cactus!"
		- "&5%n&7 tried to hug a cactus!"
		- "&5%n&7 needs to be more careful around cactuses!"
		- "&5%n&7 felt the wrath of Cactus Jack!"
		- "&5%n&7 learned the result of rubbing a cactus!"
		- "&5%n&7 died from cactus injuries!"
		- "&5%n&7 poked himself with a cactus...and died."
		- "&5%n&7 ran into some pointy green stuff that wasn't grass."
		- "&5%n&7 was distracted by a tumble weed and died by cactus."
	  creeper:
		- "&5%n&7 was creeper bombed!"
		- "A creeper exploded on &5%n&7!"
		- "A creeper snuck up on &5%n&7!"
		- "A creeper tried to make love with &5%n&7...mmm."
		- "&5%n&7 just got the KiSSssss of death!"
		- "&5%n&7 tried to hug a creeper!"
		- "&5%n&7 is frowning like a creeper now!"
	  drowning:
		- "&5%n&7 drowned"
		- "&5%n&7 become one with the ocean!"
		- "&5%n&7 sunk to the bottom of the ocean."
		- "&5%n&7 went diving but forgot the diving gear!"
		- "&5%n&7 needs swimming lessons."
		- "&5%n 's&7 lungs have been replaced with H20."
		- "&5%n&7 forgot to come up for air!"
		- "&5%n&7 is swimming with the fishes!"
		- "&5%n&7 had a surfing accident!"
		- "&5%n&7 tried to walk on water."
		- "&5%n&7 set a record for holding breath under water."
	  enderman:
		- "&5%n&7 looked at a enderman the wrong way."
		- "An enderman pulled &5%n&7 leg..... off!"
	  fall:
		- "&5%n&7 tripped and fell...down a cliff."
		- "&5%n&7 leapt before looking."
		- "&5%n&7 forgot to bring a parachute!"
		- "&5%n&7 learned to fly...briefly..."
		- "&5%n&7 felt the full effect of gravity."
		- "&5%n&7 just experienced physics in action."
		- "&5%n&7 fell to his death."
		- "&5%n&7 forgot to look out below!"
		- "&5%n&7 got a little too close to the edge!"
		- "&5%n&7, gravity is calling your name!"
		- "&5%n&7 face planted into the ground!"
		- "&5%n&7 yells, 'Geronimo!'....*thud*"
		- "What goes up must come down, right &5%n&7?"
	  fire:
		- "&5%n&7 burned to death."
		- "&5%n&7 was set on fire!"
		- "&5%n&7 is toast! Literally..."
		- "&5%n&7 just got barbequed!"
		- "&5%n&7 forgot to stop, drop, and roll!"
		- "&5%n&7 is extra-crispy!"
		- "&5%n&7 spontaneously combusted!"
		- "&5%n&7 put his hands in the toaster!"
		- "&5%n&7 just got burned!"
	  fire-tick:
		- "&5%n&7 burned to death."
		- "&5%n&7 was set on fire!"
		- "&5%n&7 is toast! Literally..."
		- "&5%n&7 just got barbequed!"
		- "&5%n&7 forgot to stop, drop, and roll!"
		- "%n&7 likes it extra-crispy!"
		- "&5%n&7 spontaneously combusted!"
		- "&5%n&7 put his hands in the toaster!"
		- "&5%n&7 just got burned!"
	  ghast:
		- "&5%n&7 was blown to bits by a ghast."
		- "Those aren't babies you hear, &5%n&7!"
		- "&5%n&7 was killed by a ghostly hadouken!"
		- "&5%n&7 just got exploded by a fireball!"
		- "&5%n&7 got too comfy in the Nether!"
	  giant:
		- "&5%n&7 was stomped by a giant!"
		- "&5%n&7 was flattened by a giant!"
		- "&5%n&7 shouldn't have climbed the bean stalk."
	  lava:
		- "&5%n&7 became obsidian."
		- "&5%n&7 was caught in an active volcanic eruption!"
		- "&5%n&7 tried to swim in a pool of lava."
		- "&5%n&7 was killed by a lava eruption!"
		- "&5%n&7 was forged into obsidian by molten lava."
		- "&5%n&7 took a dip in the wrong kind of pool!"
		- "&5%n&7 found out how to encase himself in carbonite."
		- "&5%n&7! the floor is lava! The floor is lava!"
	  lightning:
		- "&5%n&7 was struck down by Zeus' bolt."
		- "&5%n&7 was electrecuted."
		- "&5%n&7 figured out that it wasn't a pig's nose in the wall."
	  pigzombie:
		- "&5%n&7 lost a fight against a zombie pig."
		- "&5%n&7, touching a zombie pig is never a good idea."
		- "&5%n&7, looked at a pigzombie the wrong way."
	  pvp:
		- "&f%a&7 killed &5%n&7 using a(n) &3%i&7!"
		- "&f%a&7 slays &5%n&7 with a &3%i&7!"
		- "&f%a&7 hunts &5%n&7 down with a &3%i&7!"
		- "&5%n&7 was killed by a &3%i&7 wielding %a!"
		- "&f%a&7 leaves &5%n&7 a bloody mess!"
		- "&f%a&7 uses a &3%i&7 to end &5%n''s&7 life!"
		- "&5%n&7 collapses due to &3%i&7 attacks from %a!"
		- "&5%n&7 is now a bloody mess thanks to %a''s &3%i&7!"
		- "&f%a&7 beats &5%n&7 with a &3%i&7!"
		- "&5%n&7 was killed by %a''s &3%i&7 attack!"
		- "&f%a&7 defeats &5%n&7 with a &3%i&7 attack!"
		- "&f%a&7 raises a &3%i&7 and puts and end to &5%n''s&7 life!"
		- "&f%a&7 took out &5%n&7 with a &3%i&7!"
		- "&5%n&7 was victimized by &f%a''s&7 &3%i&7!"
		- "&5%n&7 was eliminated by %a''s &3%i&7!"
		- "&f%a&7 executes &5%n&7 with a &3%i&7!"
		- "&f%a&7 finishes &5%n&7 with a &3%i&7!"
		- "&f%a&7's &3%i&7 has claimed &5%n&7 as another victim!"
		- "&5%n&7 lost a savage duel to %a!"
		- "&f%a&7 has beaten &5%n&7 to a pulp!"
		- "&f%a&7 pwns &5%n&7 in a vicious duel!"
		- "&5Score %a 1 - &5%n&7 0!"
		- "&f%a&7 has defeated &5%n&7 in battle!"
		- "&5%n&7 was slain by &f%a&7!"
		- "&f%a&7 emerges victorious in a duel with &5%n&7!"
		- "&5%n&7 was pwned by &f%a&7!"
		- "&5%n&7 was killed by %a!"
		- "&5%n&7 was dominated by %a!"
		- "&5%n&7 was fragged by %a!"
		- "&5%n&7 needs more practice and was killed by %a!"
		- "&5%n&7 was beheaded by %a!"
	  pvp-fists:
		- "&f%a&7 pummeled &5%n&7 to death"
		- "&f%a&7 crusted &5%n&7 with their bare hands"
	  pvp-tamed:
		- "&5%n&7 was mauled by &f%a's&7 &3%i"
		- "&5%n''s&7 hand was bitten by &f%a's&7 &3%i"
	  silverfish:
		- "&5%n&7 was killed by a silverfish!"
		- "&5%n&7 found something hidden below a rock"
		- "&5%n&7 You can't stuff that many fish into your mouth!"
		- "&5%n&7 activated a silverfish trap"
		- "&54%n''s&7 last words  'Oh god they''re coming out of the walls!'"
	  skeleton:
		- "A skeleton shot &5%n&7 to death!"
		- "&5%n&7 was on the wrong end of the bow. "
		- "&5%n&7 had a skeleton in the closet..."
		- "&5%n&7! strafe the arrows! Strafe the arrows!"
		- "&7A skeleton just got a head shot on &5%n&7!"
	  slime:
		- "A slime found &5%n&7. The slime won."
		- "&5%n&7 wanted to play with slime. The slime wasn't happy."
	  spider:
		- "&5%n&7 is all webbed up."
		- "&5%n&7 got trampled by arachnids!"
		- "&5%n&7 got jumped by a spidah!"
		- "Spiders just climbed all over &5%n&7!"
		- "&5%n&7 forgot spiders could climb!"
	  starvation:
		- "&5%n&7 did forget to eat his lunch."
		- "&5%n&7 didn't find the next Burger."
		- "&5%n&7 became a skeleton."
		- "&5%n&7 TALKS ALL CAPITALS NOW."
	  suffocation:
		- "&5%n&7 suffocated."
		- "&5%n&7 was looking up while digging!"
		- "&5%n&7 choked to death on earth!"
		- "&5%n&7 choked on a ham sandwich"
	  suicide:
		- "&5%n&7 took matters into his own hands."
		- "&5%n&7 isn't causing NPE''s anymore."
	  unknown:
		- "&5%n&7 died from unknown causes."
		- "&5%n&7 imploded into nothingness"
		- "&5%n&7 was vaporized"
		- "&5%n&7 died from explosive diarrhea"
		- "&5%n&7 was killed by Chuck Norris"
		- "&5%n&7 was running with scissors...now he runs no more"
		- "&5%n&7 was hit by a falling piano"
		- "&5%n&7 was assasinated by a shuriken headshot from the shadow"
		- "&5%n&7 was barrel rolling...and died"
		- "&5%n&7 was killed by Cthulhu"
		- "&5%n&7 forgot to wear his spacesuit"
		- "&5%n&7 choked on a ham sandwich"
		- "&5%n&7 died at the hands of ninja assassins"
	  void:
		- "&5%n&7 died in The Void."
	  wolf:
		- "&5%n&7 became a wolf's lunch."
		- "&5%n&7 couldn't howl with the wolfs."
	  zombie:
		- "&5%n&7 was punched to death by zombies!"
		- "&5%n&7 was bitten by a zombie!"
		- "&5%n&7 fell to the hunger of the horde!"
		- "&5%n&7 Hasn't played enough L4D2!"
		- "&5%n&7 couldn't run faster than the zombie!"
	  blaze:
		- "&5%n&7 was set on fire at a blaze, well.. by a blaze!"
		- "&5%n&7 was airbombed!"
		- "&5%n&7, not everything on fire is a player!"
		- "&5%n&7 nope, that wasn't a rocket."
	  magmacube:
		- "&5%n&7 didn't expect this kind of slinky!"
		- "&5%n&7 got eaten by a cube."
		- "&5%n&7 got coombad by a cube."
	  enderdragon:
		- "&5%n&7 died at the end... IN the end."
		- "&5%n&7 looking up would have helped."
		- "Well, Anne McCaffrey didn't talk about that kind of Dragon, right &5%n&7?"
		- "No egg for you, &5%n&7."
	  dispenser:
		- "&5%n&7 got shot in the back by a dispenser!"
		- "Again the wrong weight Indi? �hm. &5%n&7"
		- "&5%n&7 thinks he is Indiana Jones."
		- "&5%n&7 felt for the booby trap."