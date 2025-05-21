# Helldivers 2 Utility Bot - Complete User & Admin Guide

This comprehensive guide covers all features of the Helldivers 2 Utility Bot, designed to enhance your Discord community with deployment tracking, squad management, minigames, and more.

## Table of Contents

- [Getting Started](#getting-started)
- [Deployment System](#deployment-system)
  - [Quick Deploy Button](#quick-deploy-button)
  - [Basic Deployment](#basic-deployment)
  - [Deployment Parameters](#deployment-parameters)
  - [Standby Mode](#standby-mode)
  - [Voice Channel Integration](#voice-channel-integration)
- [Squad Management](#squad-management)
  - [Joining Others](#joining-others)
  - [SOS System](#sos-system)
  - [Squad Voice Channels](#squad-voice-channels)
- [Social Features](#social-features)
  - [Commendation System](#commendation-system)
  - [Medal System](#medal-system)
  - [Helldiver Info Cards](#helldiver-info-cards)
  - [Bulletins/Dispatches](#bulletinsdispatches)
- [Game Management](#game-management)
  - [War Orders](#war-orders)
  - [Server Statistics](#server-statistics)
  - [Loadout System](#loadout-system)
  - [Penitent Crusades](#penitent-crusades)
- [Minigames](#minigames)
  - [Server Attack Defense](#server-attack-defense)
  - [Stratagem Crafting](#stratagem-crafting)
  - [Escape Pods](#escape-pods)
- [Administration](#administration)
  - [Initial Server Setup](#initial-server-setup)
  - [Channel Configuration](#channel-configuration)
  - [Role Management](#role-management)
  - [Moderation Tools](#moderation-tools)
  - [Attack Management](#attack-management)
  - [Stats & Orders Management](#stats--orders-management)
- [Support & Credits](#support--credits)


## ⚠️ Quick Setup Summary (Admins, Read This First)

Before anything else:
1. **DO NOT** set `/setminigamechannel` to your LFG or chat channels. It should be an isolated, low-traffic channel.
2. **DO NOT** assign general roles like `@everyone` or `@here` as LFG roles.
   - Use a specific role like `@LFG`, `@ReadyUp`, or `@HD Players`
   - If unsure, create a new one just for LFG pings.

Proper setup ensures channels aren’t spammed and players don’t get irrelevant pings.

---

## Getting Started

The HD2 Utility Bot uses Discord's slash command system. Type `/` followed by the command name to use any feature.

As a server admin, your first steps should be:
1. Set up the deployment channel with `/setchannel #channel-name`
2. Configure the minigame channel with `/setminigamechannel #channel-name`
3. Set up LFG roles with `/enablelfg @Role`
4. Set up the automatic Voice Channel category with `/setvccategory [category]`

As a user, start by:
1. Using the **Quick Deploy** button or `/deploy me` to set your status
2. Check who's playing with `/active`
3. Create your Helldiver profile card with `/helldiverinfo create`


## Deployment System

The deployment system is the core feature, tracking who's playing, looking for groups, and what they're doing.

### Quick Deploy Button

> **💡 RECOMMENDED FOR MOST USERS**

The **Quick Deploy** button provides a simple, guided setup process:

1. Find the Quick Deploy button in your server's deployment channel
2. Click it to start the deployment wizard
3. Choose "Deploy" if you're actively playing or "Standby" if you're looking for a group
4. Follow the simple step-by-step prompts to set up your status
5. Choose whether to ping the LFG role to notify others

This is the easiest and most user-friendly way to set your status in the server.

### Basic Deployment

If you prefer using commands directly:

- `/deploy me` - Set yourself as deployed (actively playing)
- `/deploy standby` - Set yourself as looking for a group
- `/undeploy` - Remove your deployment status when you're done playing
- `/status` - Check your current deployment status
- `/active` - See who's currently playing or looking for groups

The `/active` command shows both deployed and standby players in a paginated list, making it easy to find teammates.

### Deployment Parameters

When using `/deploy me`, you can customize your status with these optional parameters:

- `faction:` - Which enemy you're fighting (Terminids, Automatons, Illuminate)
- `planet:` - The planet you're deployed on (e.g., Meridia, Draupnir)
- `difficulty:` - Difficulty level (1-10) or multiple difficulties (e.g., `3,4,5`)
- `with:` - Who you're playing with (mentions or number of random players)
- `notes:` - Additional information like "farming samples" or "need help with mission"
- `friend_code:` - Your Helldivers 2 friend code for others to add you
- `ping:` - Whether to ping the LFG role (true/false)
- `grinding:` - Whether to ping the grinding role for resource farming (true/false)
- `vc_name:` - Create a temporary squad voice channel after deploying

Examples:
```
/deploy me faction:Terminids planet:Meridia difficulty:7 notes:Farming samples
/deploy me with:@Friend1 @Friend2 ping:true
/deploy me difficulty:9 grinding:true notes:Farming Super Samples
```

You can also update individual fields without touching others:
```
/deploy planet:Draupnir  (changes just your planet)
/deploy faction:Automatons  (changes just your faction)
/deploy difficulty:5  (changes just your difficulty)
/deploy notes:Need experienced players  (changes just your notes)
/deploy ping:true  (toggles LFG ping without changing other fields)
```

### Standby Mode

When you're not actively playing but want to find a group:

```
/deploy standby faction_prefs:Terminids,Automatons difficulty_prefs:3,4,5 notes:Looking for casual play
```

Parameters:
- `faction_prefs:` - Preferred enemies (comma-separated)
- `difficulty_prefs:` - Preferred difficulty levels (comma-separated)
- `comms:` - Communication preferences (e.g., "Discord voice required")
- `notes:` - Additional information 
- `ping:` - Whether to ping the LFG role (true/false)
- `grinding:` - Whether to ping the grinding role (true/false)

Your standby status will be visible to others in the `/active` list, making it easy for them to invite you.

### Voice Channel Integration

The bot monitors voice channel activity for enhanced features:

- When you join a voice channel while deployed, it updates your status
- When you leave a voice channel while deployed, your deployment will expire after 10 minutes unless you rejoin or use a command
- The bot provides a message with a countdown when your deployment is set to expire

## Squad Management

### Joining Others

To join another player's deployment:

```
/join @Username
```

This will:
1. Update your status to match theirs (faction, planet, difficulty)
2. Notify them that you've joined their squad
3. Update their status to show you're with them
4. Update the active list to show you're in a group together
5. (If they have a squad voice channel) Provide you with an invite link

When you're in a squad:
- All field updates (planet, faction, etc.) sync to all members
- You can create a squad name with `/setgroupname SquadName`

### SOS System

When you need immediate assistance:

```
/sos
```

This will:
1. Change your status to SOS mode
2. Send an urgent alert to the deployment channel
3. Ping the LFG role for maximum visibility
4. Show you in the active list with an SOS indicator

To respond to an SOS:

```
/respond @Username
```

This will:
1. Update your status to match theirs
2. Notify them that you're responding
3. Join their squad automatically
4. Provide voice channel access if available

### Squad Voice Channels

Create a temporary voice channel for your squad:

```
/deploy me vc_name:SquadName
```

This creates a voice channel named "Squad SquadName" (in this example) with a limit of 4 users. The channel will:
- Automatically delete when empty
- Be linked to your deployment status
- Be accessible to those who join your squad

If you're already in a voice channel, you'll be moved to the new squad channel automatically.

## Social Features

### Commendation System

Commendations allow players to recognize helpful teammates:

```
/commend @Username
```

Requirements:
- You must be deployed to give commendations
- You can only commend someone once every 2 hours
- You and the recipient must be deployed in the same squad
- You can't commend yourself or bots

View commendations:
- `/commendations` - Shows the commendation leaderboard
- `/showcommendations @Username` - View a specific user's commendations

As commendations accumulate, users earn special descriptions based on their total:
- 0: "No commendations yet. Keep working with your team!"
- 1-14: "A promising Helldiver with teamwork potential."
- 15-29: "A reliable squad member who supports their team."
- 30-49: "A valuable squadmate known for excellent teamwork."
- 50-99: "A distinguished Helldiver with exceptional support skills."
- 100+: "A living legend of coordination and camaraderie."

### Medal System

Medals are special awards given by admins to recognize achievements:

#### User Commands:
- `/medal` - View your own medals
- `/medal view @Username` - View someone else's medals
- `/medal details "Medal Name" @Username` - View details for a specific medal
- `/medal leaderboard` - See the medal leaderboard

Medals come in different types:
- **Valor**: Acts of exceptional courage in battle
- **Service**: Dedication and commitment to the mission
- **Distinction**: Outstanding performance of duties
- **Honor**: Heroic actions above and beyond the call of duty
- **Merit**: Excellence in technical or support roles

Each medal has a custom name, citation, and optional emoji that appears on the player's medal display.

### Helldiver Info Cards

Create and customize your Helldiver profile card:

```
/helldiverinfo create level:50 title:Commander enlistment_date:2023-10-15 primary:"AR-23 Liberator" quote:"For Democracy!" clans:"14th Ursine Corps" preferred_enemies:Terminids fav_stratagem:"Orbital Precision Strike" support:"EAT-17" homeworld:Earth
```

Update individual fields:
- `/helldiverinfo set-level 55` - Update your level
- `/helldiverinfo set-title "General"` - Change your title
- `/helldiverinfo set-enlistment 2023-12-01` - Change enlistment date
- `/helldiverinfo set-homeworld "Mars"` - Change your home planet
- `/helldiverinfo set-quote "No democracy without liberty"` - Change your quote
- `/helldiverinfo set-stratagem "Orbital Barrage"` - Change favorite stratagem
- `/helldiverinfo set-support "Recoilless Rifle"` - Change favorite support weapon

Add special icons:
- `/helldiverinfo set-rank-icon` - Choose from military ranks (Cadet to General)
- `/helldiverinfo set-special-icon` - Choose from special designations (like ViperCommando)

View cards:
- `/helldiverinfo show` - See your own card
- `/helldiverinfo show @Username` - View someone else's card

The cards show a futuristic date (Earth year + 160) for the enlistment date to match Helldivers lore.

### Bulletins/Dispatches

Bulletins (or "Dispatches") are cross-server announcements that allow approved servers to share news:

```
/bulletins
```

This displays the bulletin board showing messages from all approved servers in the network.

> **Note**: Only approved servers can post bulletins. Contact the bot owner through the support server to get your server approved.

For approved servers (admin commands):
- `/bulletin Your message here` - Post/update your guild's bulletin
- `/clearbulletin` - Remove your guild's bulletin
- `/clearbulletinchannels` - Remove this channel from bulletin tracking

Bulletins automatically expire after 7 days if not updated.

## Game Management

### War Orders

War Orders are server-wide objectives that players can work toward together:

#### User Commands:
- `/orders` - View the current order
- `/orders view` - View detailed progress toward current order goals

Orders can include:
- Specific faction targets (e.g., "Eliminate Terminids")
- Planet destinations (e.g., "Defend Meridia")
- Statistical goals (e.g., Kill X enemies, collect Y samples)
- Time limits (orders expire after a set time)

Progress is tracked with progress bars showing completion percentage for each objective and overall completion.

### Server Statistics

Track your server's collective achievements:

```
/stats
/stats show
```

Statistics tracked include:
- Total kills (bug_kills + bot_kills + squid_kills)
- Bug kills (Terminids)
- Bot kills (Automatons)
- Squid kills (Illuminate)
- Sample collections (common, rare, super)
- Missions completed
- Operations completed
- Side objectives completed
- Helldivers KIA

These stats integrate with the War Orders system.

### Loadout System

Manage your Helldivers 2 loadout and generate random configurations:

#### Tracking Unlocked Items:
First, mark which items you've unlocked:
```
/loadout unlock
```
This opens an interactive menu to select your unlocked items by category:
- Primary weapons
- Secondary weapons
- Throwables
- Stratagems
- Boosters
- Armor
- Cape

For quick setup, unlock entire Warbond packs:
```
/loadout unlockwarbond
```

#### Generating Random Loadouts:
Once you've set up your unlocked items:
```
/loadout random
```

This generates a balanced loadout including:
- Primary weapon
- Secondary weapon
- Throwable
- 4 stratagems (with rules to prevent incompatible combinations)
- Optional: booster, armor, cape

#### Creating & Sharing Loadouts:
Create a custom loadout to share with others:
```
/loadout create "Anti-Tank Specialist" "Loadout optimized for vehicle destruction"
```

The command guides you through an interactive selection process to build and share your loadout.

#### Managing Your Collection:
Remove items from your unlocked list:
```
/loadout remove
```

### Penitent Crusades

The Penitent Crusade is a progression system where you complete increasingly difficult missions to earn better equipment. But beware - failure means losing your hard-earned gear!

#### Getting Started with Crusades

- **Starting a Crusade**:
  ```
  /crusade start "Name of your crusade"
  ```
  This creates your personal crusade journey with basic starter equipment.

- **Joining a Crusade**:
  ```
  /crusade join @Username
  ```
  Join another player's crusade (only possible at the beginning of their crusade).

- **Viewing Crusade Status**:
  ```
  /crusade status
  ```
  View your current crusade progress, equipment, and mission level.

- **Listing Active Crusades**:
  ```
  /crusade list
  ```
  See all active crusades in the server with their progress.

#### Playing the Crusade

- **Completing Missions**:
  ```
  /crusade complete
  ```
  Report a successful mission with max stars to earn rewards. Each member gets to choose a reward!

  ```
  /crusade complete max_stars:false
  ```
  Report a completed mission without max stars (no rewards, just mission progression).

- **Failed Missions**:
  ```
  /crusade fail
  ```
  Report a failed mission. Each squad member must sacrifice an item, and your mission counter decreases.

- **Specialists**:
  ```
  /crusade specialists
  ```
  Choose a specialist class with unique starting equipment. Only available at the beginning of normal crusades or during the first 3 missions of super crusades.

#### Specialists and Equipment

**Available Specialists**:
- **The Zealous Martyr**: Explosive specialist willing to sacrifice for the cause
- **The Permacura Rep**: Medic specialist with advanced healing technologies
- **The Flag Bearer**: Morale booster who carries Super Earth's flag with pride
- **The Viper Commando**: Stealth specialist with precision weapons
- **The Speedrunner**: Specialized in quick mission completion and extraction
- **The Pyromaniac**: Master of fire-based weapons and tactics
- **The Lightning Bug**: Electrical weapons expert with shocking capabilities
- **The Scout Sniper**: Long-range specialist with reconnaissance abilities
- **The Truth Enforcer**: Enforcer of Super Earth's ideals with crowd control weapons
- **The Exterminator**: Toxic gas specialist dedicated to bug elimination
- **The Assault Trooper**: Frontline fighter specializing in adaptability
- **The Loot Goblin**: Resource gatherer focused on sample collection
- **The Escape Artist**: Mobility specialist who excels at evasion

**Equipment Tiers**:
- 🌟 **S-Tier**: Extremely rare and powerful equipment
- ⭐ **A-Tier**: Powerful, high-quality equipment
- 🔹 **B-Tier**: Solid, reliable equipment
- 🔸 **C-Tier**: Basic, common equipment

Equipment is divided into categories:
- Stratagems (weapons, defenses, orbital strikes)
- Primary weapons
- Secondary weapons
- Throwables
- Armor passives
- Boosters

#### Crusade Management

- **Pausing Your Crusade**:
  ```
  /crusade pause
  ```
  Pause your active crusade for later continuation.

- **Resuming Your Crusade**:
  ```
  /crusade resume
  ```
  Resume a paused crusade. All members must ready up to continue.

- **Leaving a Crusade**:
  ```
  /crusade leave
  ```
  Leave a crusade you've joined (cannot leave your own crusade).

- **Abandoning Your Crusade**:
  ```
  /crusade abandon
  ```
  Permanently abandon your crusade (all progress and equipment lost).

- **Getting Help**:
  ```
  /crusade help
  ```
  View the detailed crusade guide.

#### Crusade Progression

1. Normal crusades progress through 21 increasingly difficult missions
2. Mission difficulty increases as you complete more missions:
   - Missions 1-2: Medium (Level 3)
   - Missions 3-5: Hard (Level 4)
   - Missions 6-8: Very Hard (Level 5)
   - Missions 9-11: Extreme (Level 6)
   - Missions 12-14: Suicide (Level 7)
   - Missions 15-17: Helldive (Level 9)
   - Missions 18-21: Super Helldive (Level 10)

3. Complete all 21 missions to unlock Super difficulty
4. Super difficulty starts at higher levels and progresses faster

**Success and Failure**:
- Success with max stars: Earn equipment rewards (rarer equipment becomes available at higher mission levels)
- Success without max stars: Progress mission counter without rewards
- Failure: Lose equipment and mission counter decreases

Remember to report your mission outcomes honestly for the true Penitent Crusade experience!

## Minigames

### Server Attack Defense

The Server Attack minigame simulates defensive scenarios:

1. Admins create an attack with requirements for defensive supplies
2. Players craft and donate supplies to defend against the attack
3. If enough supplies are gathered before the time expires, everyone succeeds
4. If not enough supplies are gathered, all players lose their inventory

#### User Commands:
- `/givesupplies supply:Orbital Precision Strike quantity:2` - Donate supplies to defense
- `/givesupplies category:offensive quantity:3` - Donate random supplies of a category
- `/attackshow` - Show the current attack status

The supplies are categorized as:
- **Offensive**: Combat-focused stratagems
- **Defensive**: Protection and fortification stratagems
- **Support**: Utility and assistance stratagems

### Stratagem Crafting

In the designated minigame channel, craft stratagems by typing their directional sequences:

Examples:
- `→→↑` - Craft an Orbital Precision Shell
- `↑→↓↓↓` - Craft an Eagle 500kg Bomb

Each successfully crafted stratagem is added to your inventory, which you can view with:
```
/equipment
/equipment @Username
```

To see available stratagems:
```
/liststratagems
```

#### Boosters:
Found in escape pods or awarded by admins, boosters multiply your crafting output:
- **Double**: Produces 2× the normal output
- **Triple**: Produces 3× the normal output

Activate a booster:
```
/booster booster_type:double duration:30
```

Check active boosters:
```
/showboosters
```

Multiple boosters stack multiplicatively - having both a double and triple active would give 6× output!

### Escape Pods

Escape pods randomly spawn in the minigame channel:
1. A message appears: "🚀 An Escape Pod Drifts In…"
2. Type `SALUTE` to claim its contents
3. The first person to respond gets the reward

Possible contents:
- Random stratagems (1-5 of various types)
- Crafting boosters (double or triple, with durations from 5-60 minutes)

Admins can manually spawn pods with specific contents for events or rewards.

### ⚠️ Important Setup Note
> The `/setminigamechannel` command must **not** be used in high-traffic channels (like LFG or general chat). This channel will receive:
> - Stratagem crafting inputs
> - Escape pod messages
> - Booster messages
> - Supply contribution messages
>
> Choose or create a **dedicated minigame channel** for these features to prevent clutter and confusion.

(*Keep rest of minigames section unchanged*)

---
## Administration

### Initial Server Setup

**1. Set Deployment Channel**
```
/setchannel #deployment-channel
```
- Sends deployment status, SOS alerts, and Quick Deploy buttons
- Should be a central channel, dedicated to users looking to group up.

**2. Set Minigame Channel**
```
/setminigamechannel #minigames
```
- ❌ **Never use LFG or a General Chat**
- ✅ Use a dedicated channel (e.g., `#stratagem-lab`, `#minigames`, `#stratagem-clicker`, `#bot-minigames`)

**3. Set Welcome Channel**
```
/setwelcomechannel #welcome
```
- New members get a brief greeting embed here

**4. Configure VC Category**
```
/setvccategory "Squad Channels"
```
- Admins can use this to select which category new voice channels will be created under.

**5. Set LFG Role**
```
/enablelfg @LFG
```
- ❌ Do NOT use `@everyone` or roles that include every server member
- ✅ Create a new role if necessary (`@Helldivers`, `@LFG`, `@deployments`)

**6. Set Grinding Role (optional)**
```
/enablegrindrole @Grinding
```
- Like the LFG role, this should be a **specific role**, not a general one

**7. (Optional) Configure Status Counters**
```
/setstatuscounters deployed_channel:"Deployed Count" standby_channel:"Standby Count" assist_channel:"Assisting Count"
```
- These should be voice channels that are dedicated, in view, not mixed with other channels and set so that users cannot connect, but can see.
---

### Channel Configuration

Detailed explanation of channel setup commands:

- `/setchannel #channel` - Sets where deployment statuses appear
  - Creates the Quick Deploy button
  - Deployment status cards appear here
  - LFG and SOS alerts are sent here

- `/setminigamechannel #channel` - Sets where minigames occur
  - Stratagem crafting sequences work here
  - Escape pods spawn here
  - Attack notifications appear here

- `/setwelcomechannel #channel` - Sets where welcome messages appear
  - New member welcome embeds appear here

- `/createactivelist` - Creates a persistent, auto-updating list of active players in the current channel

- `/orders channel` - Sets the current channel for order notifications

- Keep deployment and minigame activity separate from main server activity channels.

### Role Management

- `/enablelfg @Role` - Sets the role to ping for LFG notifications
  - This role is pinged when users deploy with `ping:true`
  - It's also pinged for SOS calls
  - Members can opt to ping this role by default with `/setlfgpref true`

- `/disablelfg` - Removes the LFG role setting

- `/enablegrindrole @Role` - Sets the role for grinding notifications
  - Pinged when users deploy with `grinding:true`
  - Useful for organizing farming groups

- `/disablegrindrole` - Removes the grinding role setting

**✅ GOOD Role Examples:**
- `@LFG`, `@HD Players`, `@Ready to Drop`

**❌ BAD Role Examples:**
- `@everyone`, `@Members`, `@Gamers` (broad roles)

Explain the purpose of the role in your server rules/pings so users can opt in/out.

---


### Moderation Tools

The bot includes several themed moderation commands:

- `/execute @user reason:Reason` - Ban a user (with Super Earth justice flavor)
  - Creates a court martial declaration embed
  - Bans the user from the server
  - Logs the execution in server records

- `/executions` - View the log of recent executions

- `/censor @user length:HH:MM reason:Reason` - Timeout a user (speech-crime thematic)
  - Creates a "Speech Censorship Citation" embed
  - Applies a Discord timeout for the specified duration
  - Multiple users can be censored simultaneously

- `/censoredusers` - View users currently in timeout

- `/exile @user reason:Reason` - Kick a user (exile thematic)
  - Creates an "Exile Order" embed
  - Kicks the user from the server

- `/lockdown` - Toggle a 5-second slow-mode in the current channel
  - Useful for controlling chat flow during busy times

- `/surveillancereport` - View the server's audit log in a paginated format

### Attack Management

Create and manage attack events (admin only):

```
/attack create name:"Terminid Invasion" req_offensive:10 req_defensive:15 req_support:5 time_left:02:00 description:"Terminids are invading!" planet:Meridia faction:Terminids
```

Parameters:
- `name:` - Friendly name for the attack
- `req_offensive:` - Required offensive supplies
- `req_defensive:` - Required defensive supplies
- `req_support:` - Required support supplies
- `time_left:` - Duration before attack expires (HH:MM or DD/MM HH:MM)
- `description:` - Optional details
- `planet:` - Optional planet name
- `faction:` - Optional attacking faction

Other attack management commands:
- `/attack end` - End the current attack (with outcome: auto, success, or failure)
- `/attack help` - Show help for attack commands
- `/spawnpod` - Manually spawn an escape pod with specific contents

### Stats & Orders Management

#### Medal Administration:
- `/medal award @user medal_type:valor citation:"For exceptional courage" medal_name:"Heart of Steel" emoji:🎖️` - Award a medal
- `/medal createpreset medal_type:valor medal_name:"Heart of Steel" emoji:🎖️ citation:"For exceptional courage"` - Create a medal preset
- `/medal awardpreset @user "Heart of Steel"` - Award a preset medal
- `/medal listpresets` - List available medal presets
- `/medal deletepreset "Heart of Steel"` - Delete a medal preset
- `/medal edit @user "Heart of Steel" new_name:"Steel Heart" citation:"Updated citation"` - Edit a medal

#### Order Management:
- `/orders create title:"Operation Firestorm" text:"Eliminate Terminid presence on Meridia" until:"MM/DD HH:MM" planets:"Meridia,Draupnir" factions:"Terminids"` - Create a new order
- `/orders stats bug_kills:500 bot_kills:250 squid_kills:100` - Update order statistics
- `/orders goals bug_kills:1000 bot_kills:500 squid_kills:200` - Set goals for order statistics
- `/orders clear` - Clear the current order
- `/orders reset` - Reset order statistics

#### Stats Management:
- `/stats add bug_kills:100 bot_kills:50 missions_completed:5` - Add to server-wide statistics
- `/stats reset` - Reset all server statistics (requires confirmation)


## Support & Credits

- **Support Server**: https://discord.gg/Qfdn4rWAt2
- **Documentation**: https://thexant.github.io/BotReadme/
- **Bot by**: Vetaso & Gohan
- **Special thanks**: Members of the Freedom Alliance and specifically, the '14th Ursine Corps'

Clan leaders interested in getting their clan added to the bulletin system and logo added to player cards should contact Vetaso (thexant) in the support server.
