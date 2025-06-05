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
  - [Stratagem Crafting & Leveling System](#stratagem-crafting--leveling-system)
  - [Mission System](#mission-system)
  - [Economy & Trading System](#economy--trading-system)
  - [Escape Pods](#escape-pods)
  - [Weapons & Armor System](#weapons--armor-system)
  - [Server Attack Defense](#server-attack-defense)
  - [Additional Features](#additional-features)
- [Administration](#administration)
  - [Initial Server Setup](#initial-server-setup)
  - [Moderation Tools](#moderation-tools)
  - [Attack Management](#attack-management)
  - [Stats & Orders Management](#stats--orders-management)
- [Support & Credits](#support--credits)


## ⚠️ Quick Setup Summary (Admins, Read This First)

Before anything else:
1. **DO NOT** set your minigame channel to your LFG or chat channels. It should be an isolated, low-traffic channel.
2. **DO NOT** assign general roles like `@everyone` or `@here` as LFG roles.
   - Use a specific role like `@LFG`, `@ReadyUp`, or `@HD Players`
   - If unsure, create a new one just for LFG pings.

Proper setup ensures channels aren’t spammed and players don’t get irrelevant pings.

---

## Getting Started

The HD2 Utility Bot uses Discord's slash command system. Type `/` followed by the command name to use any feature.

As a server admin, your first step should be to run the setup wizard using `/setup` and configure the bot to your liking. Most of the steps are optional.

As a user, start by:
1. Using the **Quick Deploy** button to set your status
2. Check who's playing with `/active`
3. Create your Helldiver profile card with `/helldiverinfo create`


## Deployment System

The deployment system is the core feature, tracking who's playing, looking for groups, and what they're doing.

### Quick Deploy Button

> **💡 RECOMMENDED FOR MOST USERS**

The **Quick Deploy** button provides a simple, guided setup process:

1. Find the Quick Deploy button in your server's deployment channel, or create a new one with `/deploy button`
2. Click it to start the deployment wizard
3. Choose "Deploy" if you're actively playing or "Standby" if you're looking for a group
4. Follow the simple step-by-step prompts to set up your status
5. Choose whether to ping the LFG role to notify others
6. Choose whether to notify other servers that have Global LFG enabled (if yours does).
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
- `global` - whether to deploy globally, omitting this defaults deployments to local.

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

To join another player's deployment press the green ***JOIN*** button below their status.

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

Create a temporary voice channel for your squad by setting Squad Comms in the Quick Deploy Wizard, or using `/squadvc SquadName`

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

### Martyrs System
Similar to commendations, Martyrs let you recognize when teammates give the ultimate sacrifice for democracy.
You must be deployed and in a group with team members to engrave their name on the "Wall of Martyrs".
- `/martyr @user` - Add a user to the Wall of Martyrs
- `/wallofmartyrs` - View your servers wall of Martyrs

  
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
- `/helldiverinfo edit`

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
  Join another player's crusade (CURRENTLY NOT FUNCTIONAL AND REMOVED FOR FIXING).

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
  Leave a crusade you've joined (command removed until group crusades are fixed).

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

The minigame system has been completely overhauled with multiple interconnected systems including stratagem crafting with progression, dynamic missions, player economy, and server defense events.

### Stratagem Crafting & Leveling System

In the designated minigame channel, craft stratagems by typing their directional sequences to gain XP and unlock new equipment:

Examples:
- `→→↑` - Craft an Orbital Precision Shell
- `↑→↓↓↓` - Craft an Eagle 500kg Bomb

**Leveling System:**
- Gain XP from crafting: **Offensive stratagems** give 2 XP, **Defensive/Support** give 1 XP
- Level up to unlock new stratagems and equipment
- View your progress with `/level` or `/level @Username`
- Check what you can craft with `/craftable` or `/cancraft [stratagem_name]`

**Level Commands:**
- `/level` - View your crafting level and XP progress
- `/craftable` - Show stratagems you can currently craft
- `/cancraft [stratagem_name]` - Check if you can craft a specific item
- `/liststratagems [level_filter]` - List all craftable stratagems by level

**Equipment Management:**
- `/equipment` - View your crafted equipment inventory
- `/equipment @Username` - View someone else's equipment

#### Boosters:
Boosters multiply your crafting output and are found in escape pods:
- **Double**: Produces 2× the normal output  
- **Triple**: Produces 3× the normal output

- Example of activating a booster: `/booster booster_type:double duration:30`
- To check active boosters: `/showboosters`
Multiple boosters stack multiplicatively!

### Mission System

Dynamic missions spawn periodically offering XP and requisition rewards:

**Mission Flow:**
1. Missions spawn randomly in the minigame channel with a **🎯 Claim Mission** button
2. First player to claim gets 30 minutes to select their loadout
3. Choose equipment from your inventory (requires 1 weapon + 1 armor minimum)
4. Mission executes automatically with real-time progress updates
5. Success depends on your equipment power vs mission difficulty

**Mission Commands:**
- `/mission status` - Check current mission status
- `/mission help` - Show mission system guide
- `/requisition` - Check your requisition currency balance

**Admin Mission Commands:**
- `/spawnmission` - Manually spawn a mission with custom parameters
- `/clearmission` - Clear the current active mission
- `/missioninfo` - Show detailed mission information

Missions have different objectives (Destroy, Extract, Defend, Infiltrate, Sabotage), environments (Urban, Desert, Jungle, Arctic, Industrial), and optional modifiers that affect difficulty and rewards.

### Economy & Trading System

#### Shop System

Use requisition currency to buy and sell items with other players:

**Shopping Commands:**
- `/shop browse` - Open the interactive shop interface with:
  - **🛒 User Listings**: Items sold by other players
  - **🎲 Rotating Stock**: Limited-time items from the Requisitions Officer (rotates every 6 hours)
  - **📦 My Listings**: Manage your own sales

- `/shop list [item] [quantity] [price]` - List an item for sale
- `/shop help` - Learn about the shop system

**Example:**
`/shop list item:"Orbital Laser Heatsink" quantity:2 price:500`
#### Trading System

Direct player-to-player item trading:

- `/trade offer @user [item] [quantity]` - Offer a trade to another player
- `/trade accept [trade_id]` - Accept a trade offer
- `/trade cancel [trade_id]` - Cancel your trade offer  
- `/trade list` - View pending trades involving you
- `/trade history` - View your recent trade history

**Example:**
`/trade offer @Friend item:"Eagle 500kg Bomb" quantity:3`
Trades expire after 24 hours if not accepted.

### Escape Pods

Two types of escape pods spawn in the minigame channel:

#### Normal Escape Pods
- Spawn hourly with 25% chance if no pod exists
- Type `SALUTE` to claim contents
- Rewards: Random stratagems, boosters, XP, and requisition currency

#### Rare Escape Pods  
- Spawn every 4 hours with 25% chance
- **⚠️ Expire after 10 minutes!**
- Contain premium rewards: **rare weapons**, **rare armor**, higher XP/requisition
- Announced with gold embed and countdown timer

**Admin Pod Commands:**
- `/spawnpod` - Spawn a normal pod with optional custom contents
- `/spawnrarepod` - Spawn a rare pod with premium rewards

### Weapons & Armor System

The minigame now includes rare weapons and armor that provide different power levels for missions:

**Rare Weapons**: Various categories including precision, energy, explosive, and incendiary types
**Rare Armor**: Different types including heavy, stealth, and standard variants  

- Everyone starts with permanent **AR-23 Liberator** (weapon) and **B-01 Tactical** armor
- Find additional weapons and armor in rare escape pods or purchase from the shop
- Different equipment provides different mission power bonuses
- Equipment is consumed when used in missions (except permanent starter gear)

### Server Attack Defense

Server-wide defense events where players contribute supplies:

**User Commands:**
- `/givesupplies supply:"Orbital Precision Strike" quantity:2` - Donate specific supplies
- `/givesupplies category:offensive quantity:3` - Donate random supplies of a category  
- `/attackshow` - Show/refresh the current attack status

**Admin Commands:**
- `/attack create` - Start a new server attack with supply requirements
- `/attack end [outcome]` - End attack (auto/success/failure)
- `/attack help` - Show attack command help

If the defense fails, all players lose their entire inventory!

### Additional Features

**Utility Commands:**
- `/roll [sides]` - Roll dice (defaults to d20, use 6 for standard die)
- `/minigamehelp` - Show overview of all minigame systems

**Admin Setup:**
  - ❌ **Never use LFG or General Chat channels**
  - ✅ **Use a dedicated channel** (e.g., `#stratagem-lab`, `#minigames`, `#bot-games`)
  - This channel receives crafting inputs, pod spawns, mission announcements

### ⚠️ Important Setup Note
> The minigame channel must **not** be used in high-traffic channels (like LFG or general chat). This channel will receive:
> - Stratagem crafting inputs (directional sequences)
> - Escape pod messages and claims
> - Mission announcements and progress
> - Shop announcements
> - Trade notifications
> - Supply contribution messages
>
> Choose or create a **dedicated minigame channel** for these features to prevent clutter and confusion in your main server channels.
---
## Administration

### Initial Server Setup
- Server setup has been streamlined into a simple Setup Wizard. Admins should use the command `/setup` to pull up the Setup Wizard.
- Changes can be made in the future to edit configuration without adjusting settings you dont change.
- Setup allows you to set your LFG channel, your minigames channel, your LFG roles, your VC Category, and almost every other configurable feature.

**✅ GOOD Role Examples:**
- `@LFG`, `@HD Players`, `@Squad`

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
- `/orders create order_id:[shortname for admin reference] title:"Operation Terminid Kill" text:"Eliminate Terminid presence on Bore Rock once and for all" until:"MM/DD HH:MM" planets:"Bore Rock" factions:"Terminids"` - Create a new order
- `/orders update [order_id]` - Update order statistics
- `/orders goals bug_kills:1000 bot_kills:500 squid_kills:200` - Set goals for order statistics
- `/orders clear` - Clear the current order
- `/orders reset` - Reset order statistics
- `/orders add_guild [order_ID] [guild_ID]` - Add another server as a participant on your order.
#### Stats Management:
- `/stats update` - Add to server-wide statistics
- `/stats reset` - Reset all server statistics (requires confirmation)


## Support & Credits

- **Support Server**: https://discord.gg/Qfdn4rWAt2
- **Documentation**: https://thexant.github.io/BotReadme/
- **Bot by**: Vetaso & Gohan
- **Special thanks**: Members of the Freedom Alliance and specifically, the '14th Ursine Corps'

Clan leaders interested in getting their clan added to the bulletin system and logo added to player cards should contact Vetaso (thexant) in the support server.
