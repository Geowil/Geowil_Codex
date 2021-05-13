# Geowil Codex Plugin V1.0 Pre-Release

### Table of Contents
[Introduction](#introduction)<br>
[What does this plugin do?](#WhatIsThis)<br>
[Requirements](#optionals)<br>
[Installation](#installation)<br>



Demo: [Version 1.0 PR](http://www.lmpgames.com/RMMV/Plugins/Geowil_Codex_1_0_Demo.zip)<br>
Project: [Version 1.0 PR](http://www.lmpgames.com/RMMV/Plugins/Geowil_Codex_V1_0_Project.zip)<br><br>


<a name="Intoduction"/><br>
#### Introduction<br>
Welcome to the GitHub repo for my latest, and largest, plugin to date!  Please note that this plugin is in a Pre-Release state and is subject to change and may
contain anything from game breaking bugs to functionality that doesn't function as intended yet.  These risks increase as you enable more of the systems within the plugin
so please be aware and on the lookout.<br><br>

If you happen to find any issue, please let us know on the Issues tab above.<br><br>

---

<a name="WhatIsThis"/><br>
#### What does this plugin do?<br>
This plugin is designed to take one of the more annoying aspects of RPG Maker and give you an easy way to handle it.  I am speaking about game lore.<br><br>

Game lore is one of those things most RPG Maker devs run screaming from because of the very bad ways in which it has to be implemented.  RPG Maker, for many years, has not
had an easy way to display information to the player leaving many to use events that only impart information to the player at the time of their interaction with the event (for
example, a bookshelf).  Another way is by using images created in an image editor that have information on them that are then displayed to the player.  These are likewise hard to maintain.

The last option is a plugin.  Like this one.  Through out the various versions of RPG Maker there have been dozens of plugins that track in-game information be it lore or just general information about found items, seen enemies, and the like.  This plugin intends to be a one-stop-shop; containing not only a lore codex, but also various "books" that will allow your players to see various information on enemies, weapons, items, and more.<br><br><br>

---

<a name="Requirements"/><br>
#### Requirements<br>
The only had requirements for this plugin is that you need YanFly's Message Core (YEP_MessageCore).  There are some optional plugins required if you turn on certain features.  See the next section.<br><br><br>

---

<a name="optionals"/><br>
#### Optional Plugin Requirements<br>
##### Advanced Weapon Plugin (Geowil_AWP) support - Needed if you enable AWP enhanced plugin features<br>
##### Enemy Levels (YEP_EnemyLevels) support - Needed if you enable Enemy Levels enhanced plugin features<br>
##### Main Menu Manager (YEP_MainMenuManager) support - Needed if you enable opening Codex from menu<br><br><Br>
  
---
  
<a name="installation"/><br>
#### Installation<br>
The first step for installation is to drop the Geowil_Codex.js and YEP_MessageCore.js files into your plugins folder.  All YanFly and other third\-party plugins are ***not*** provided to you.  You will need to source these yourself.  The AWP is included in the project file for this plugin but please be aware that the version included is currently not functional.  Please leave the AWP Enabled plugin setting set to false for the time being.<br><br>

##### Configuration<br>
This plugin requires some configuration for proper use.  How complex this process is depends on your needs.  If you simply need to show some information to the player, configuration is fairly straight forward.  If you are enabling everything this plugin cna do, it will be much more complex.<br><br>

The first thing you should configure is your codex heiarchy.  Currently this is present in the JS file for this version.  The hierarchy is law, it tells the plugin how to structure your codex data and allows you to set up several plugin settings in order to link your categories to the RPG Maker MV database for items, weapons, and the like.<br><br>

By default, the hierarchy is set up like below:<br>
```Javascript
  var catHierarchy = {
	'World': {
		"Lore" : "Lore"
	},
	"Equipment" : {
		"Weapons" : {
			"Daggers" : "Dagger",
			"Swords" : "Sword",
			"Flails" : "Flail",
			"Axes" : "Axe",
			"Whips" : "Whip",
			"Canes" : "Cane",
			"Bows" : "Bow",
			"Crossbows" : "Crossbow",
			"Guns" : "Gun",
			"Claws" : "Claw",
			"Gloves" : "Glove",
			"Spears" : "Spear"
		},
		"Armor" : {
			"General Armor" : "General Armor",
			"Magic Armor" : "Magic Armor",
			"Light Armor" : "Light Armor",
			"Heavy Armor" : "Heavy Armor",
			"Small Shields" : "Small Shield",
			"Large Shields" : "Large Shield"
		},
		"Accessories" : {
			"Rings" : "Ring",
			"Necklaces" : "Necklace"
		}						
	},
	"Items" : {
		"Collectables" : "Collectable",
		"Key Items" : "Key Item",
		"Consumables" : "Consumables",
		"Materials" : "Material",
	},
	"Classes" : "Classes",
	"Abilities" : {
		"Skills" : "Skill",
		"Magic" : "Magic"
	},
	"Bestiary" : {
		"Normal" : "Normal",
		"Boss" : "Boss",
		"Optional":"Optional"
	},
	"Misc" : {
		"Status Effects" : "Status Effect"
	}
};
```

That probably looks daunting right now, and it kind of is but lets break it down so you can understand what is going on and see how you can customize the codex to your needs.<br><br>

First and formost, the codex heierarchy is what is known as a map in programming.  It has a key, this key is connected to a value and the key is used to retrieve the value from the map.  In the case of above,  anything to the left of a : is a key.  Anything to the right, those are values.  These are called key/value pairs.<br><br>

So for the "World" key, there is another map as the value that contains the key/value pair "Lore" : "Lore".  World is main category, it will be displayed on the first selection menu of the codex.  The values World, in this case just Lore, will be displayed in a secondary window after World is selected.  Once Lore itself is selected, a list of all of the codex entries set up with the main category World and subcategory Lore will be displayed.<br><br>

So what about the others?  Like Equipment, that has two layers to it.  Its the same basic principle, but this time once Equipment is selected from the main Codex selection window, there will be two secondary menues to go through.  The first one will display the subcategories from the Equipment value.  Once you select one of those, the next secondary screen shows you a list of the subcategories for that selection.<br><br>

So, if you picked Equipment > Armor then the next screen would show you a list containing General Armor, Magic Armor, etc.  After selecting one of those, all of the armor of that type you have set up in the RPG Maker MV database will be displayed along with information about them.<br><br>

The heirarchy is completely customizable.  You can name your main and subcategories whatever you want so long as you set up the related plugin settings to link your categories to either database objects or to types that you can define in some other settings.  For example, Item types are completely customizable in the codex.  These types may not show up anywhere else but it will allow you to have greater control over how they are presented to the player.<br><br>


##### Configuring the category structs<br>
Once you have established your hierarchy, you will need to modify two plugin settings from within the JS file.  You can find these by searching for the following:<br><br>
```
struct~MainCats
struct~SubCats
```

For your sub categories, you only need to add the ones you created for you "Lore" category.  In the case of the example hierarcy above, the only thing we would need to change is to add "Lore" as a subcategory to the options list:<br>

```Javascript
/*~struct~SubCats:
* @param Cat
* @desc Category this entry belongs to
* @type combo
* @option Lore
* @default ""
*/
```

If you added another subcategory to "World" or whatever you renamed "World" to, you would also put it here.  For example, say we added a Story subcategory to the hierarchy:<br><br>

```Javascript
'World': {
		"Lore" : "Lore",
    "Story" : "Story"
	},
```

We would need to add that to the SubCats struct, like so:<br><br>

```Javascript
/*~struct~SubCats:
* @param Cat
* @desc Category this entry belongs to
* @type combo
* @option Lore
* @option Story
* @default ""
*/
```

If all you are using is the "lore book" functionality of the plugin then you have three more configuration changes to make.  This time from within the game editor.  Load up your game project and add in the YEP_MessageCore and Geowil_Codex plugins.  Open the Codex plugin and look for the following settings and modify them as shown given our example heierarchy with the new "Story" subcategory and having changed "World" to "History":<br><br>

Herarchy:<br>
```Javascript
'History': {
		"Lore" : "Lore",
    "Story" : "Story"
	},
```

```Javascript
/*~struct~MainCats:
* @param Cat
* @desc Category this entry belongs to
* @type combo
* @option History
* @default ""
*/
```

```Javascript
/*~struct~SubCats:
* @param Cat
* @desc Category this entry belongs to
* @type combo
* @option Lore
* @option Story
* @default ""
*/
```

Category Links:

```
"{\"History\" : \"Lore\", \"Bestiary\" : \"Enemies\", \"Abilities\" : \"Skills\", \"Classes\" : \"Classes\", \"Items\" : \"Items\", \"Weapons\" : \"Weapons\", \"Armor\" : \"Armor\", \"Accessories\" : \"Accessory\", \"Misc\" : \"Misc\"}"
```

System Links:
```
"{\"History\" : \"Lore Book\", \"Bestiary\" : \"Monster Book\", \"Abilities\" : \"Skill Book\", \"Classes\" : \"Class Book\", \"Items\" : \"Item Book\", \"Equipment\" : \"Equipment Book\", \"Misc\" : \"Misc Book\"}"
```

Override Mapping
```
"{\"Weapons\" : \"Weapons\", \"Armor\" : \"Armor\", \"Accessories\" : \"Accessories\", \"Items\" : \"Items\", \"Abilities\" : \"Skills\", \"Misc:Status Effects\" : \"states\", \"History\" : \"Lore\", \"Enemies\" : \"Enemies\", \"Bestiary\" : \"Bestiary\"}"
```

That's it.  Now you just need to create the lore entries in the plugin settings.  There are currently 114 blank entries.  Be sure to set both categories.  If you want to include white space in your entry text, use:<br><br>

```
<br>
```

Example:<br>
```
The brown fox jumped over the rabbit.<br><br>The rabbit ran off in fright.
```

More information will be added in the coming days.



