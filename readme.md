# Helldivers 2 Deployment Log Bot

A comprehensive Discord bot for Helldivers 2 communities, featuring deployment tracking, stratagem crafting, order management, and various game-themed systems.

## Table of Contents

- [Overview](#overview)
- [Setup](#setup)
  - [Inviting the Bot](#inviting-the-bot)
  - [Initial Configuration](#initial-configuration)
- [Core Features](#core-features)
  - [Deployment System](#deployment-system)
  - [Minigame System](#minigame-system)
    - [Stratagem Crafting](#stratagem-crafting)
    - [Attack Defense System](#attack-defense-system)
    - [Escape Pods](#escape-pods)
  - [War Orders](#war-orders)
  - [Medals](#medals)
  - [Server Stats](#server-stats)
  - [Temporary Squad VCs](#temporary-squad-vcs)
  - [Dispatches](#dispatches)
- [User Commands](#user-commands)
  - [Deployment Commands](#deployment-commands)
  - [Active Player Commands](#active-player-commands)
  - [Equipment & Crafting](#equipment--crafting)
  - [Attack System](#attack-system)
  - [Medal Commands](#medal-commands)
  - [Miscellaneous Commands](#miscellaneous-commands)
- [Admin Commands](#admin-commands)
  - [Server Setup](#server-setup)
  - [Deployment Administration](#deployment-administration)
  - [Order Administration](#order-administration)
  - [Medal Administration](#medal-administration)
  - [Attack Administration](#attack-administration)
  - [Stats Administration](#stats-administration)
  - [Moderation Commands](#moderation-commands)
- [Troubleshooting](#troubleshooting)
- [Credits](#credits)

## Overview

The Helldivers 2 Deployment Log Bot enhances Discord communities for Helldivers 2 players by providing:

- **Deployment Tracking**: Let others know when you're playing, your status, and find groups
- **LFG Features**: Standby mode, SOS calls, and group deployment
- **Stratagem Crafting**: Interactive minigame where players craft supplies
- **War Orders**: Create server-wide objectives for your community
- **Attack Defense**: Collaborative defense against server-wide attacks
- **Medal System**: Award and track achievements
- **Auto-deploy**: Automatic status updates when you start playing
- **Temporary Squad VCs**: Create temporary voice channels for your squad
- **Thematic Moderation**: Themed "execution" (ban) and "censorship" (timeout) commands

All features are designed to immerse your community in the Helldivers 2 universe while providing practical utility.

## Setup

### Inviting the Bot

1. Use the invitation link provided by the bot author
2. Select the server where you want to add the bot
3. Review and approve the required permissions
4. Complete the Discord authorization process

### Initial Configuration

After adding the bot to your server, administrators should configure these essential settings:

```
/setchannel                  - Set the deployment status channel
/setminigamechannel          - Set the stratagem crafting channel
/setvccategory               - Set category for temporary squad VCs
/enablelfg [role]            - (Optional) Set LFG ping role
/setstatuscounters           - (Optional) Configure voice channel status counters
/setwelcomechannel           - (Optional) Set welcome message channel
```

## Core Features

### Deployment System

The deployment system allows players to set their status, find groups, and coordinate gameplay.

**Status Types:**
- **Deployed**: Actively playing the game
- **Standby**: Available to join others
- **SOS**: Need immediate assistance

**Key Features:**
- Set faction, planet, difficulty, and more
- Group deployments for coordinated sessions
- SOS calls for emergency assistance
- Auto-deployment when Helldivers 2 is detected
- Detailed display of player status
- Status expiration and automatic cleanup
- Privacy settings for controlling who can join

### Minigame System

The minigame system provides interactive gameplay elements for your Discord community, keeping members engaged through crafting, defense, and rewards.

#### Stratagem Crafting

Players can craft stratagems by typing their directional patterns in the designated crafting channel.

**How It Works:**
1. Admin sets a dedicated channel using `/setminigamechannel`
2. Players type stratagem directional patterns (e.g., `⬇️⬇⬅️⬆️➡`) in the channel
3. The bot recognizes valid patterns and adds the stratagem to the player's inventory
4. Crafted items can be used in the Attack Defense system

**Boosters:**
- Found in Escape Pods or awarded by admins
- Multiply crafting output (2x or 3x) for a limited time
- Activated with `/booster` command
- Stack for multiplicative effects

#### Attack Defense System

Simulates attacks on your server that must be defended with player-crafted supplies.

**How It Works:**
1. Admins create an attack with `/attack create`
2. Attack requires specific numbers of offensive, defensive, and support supplies
3. Players contribute crafted items using `/givesupplies`
4. If supplies aren't gathered before the timer expires, all players lose their inventories
5. Success grants continued possession of equipment

**Supply Categories:**
- **Offensive**: Combat-focused items
- **Defensive**: Protection and fortification items
- **Support**: Utility and assistance items

#### Escape Pods

Random events that spawn in the minigame channel with rewards for players.

**How It Works:**
1. Escape pods appear randomly in the minigame channel
2. Players type "SALUTE" to claim the pod
3. Rewards include random items or boosters
4. Admins can manually spawn pods with specific contents

### War Orders

Create server-wide objectives to unite your community in common goals.

**Features:**
- Customizable title, description, and expiration
- Track statistics like kills, samples, and missions
- Set specific goals for achievement tracking
- Automatic completion tracking and notifications
- Progress visualization

### Medals

Award medals to recognize player achievements and contributions.

**Medal Types:**
- **Valor**: Exceptional courage in battle
- **Service**: Dedication and commitment
- **Distinction**: Outstanding performance
- **Honor**: Heroic actions beyond the call of duty
- **Merit**: Excellence in technical or support roles

**Features:**
- Customizable medal names and citations
- Medal tracking and display
- Leaderboard for top medal earners

### Server Stats

Track server-wide statistics for Helldivers 2 activities.

**Tracked Stats:**
- Enemy kills by faction (Terminids, Automatons, Illuminate)
- Sample collections
- Missions and operations completed
- Other milestones

### Temporary Squad VCs

Create temporary voice channels for your squad that automatically delete when empty.

**Features:**
- Create voice channels with `/squadvc [name]`
- Limited to 4 users (squad size)
- Auto-deletion when empty
- Available only to deployed or standby players

### Dispatches

Share bulletins across approved servers to coordinate larger efforts.

**Features:**
- Post server dispatches with `/bulletin`
- View dispatches from other servers with `/bulletins`
- Automatic expiration after one week

## User Commands

### Deployment Commands

```
/deploy me                   - Set your deployment status
  faction:[faction]          - Optional: Enemy faction
  planet:[planet]            - Optional: Planet name
  difficulty:[1-10]          - Optional: Difficulty level
  with:[mention/number]      - Optional: Squad members or count
  open_deploy:[true/false]   - Optional: Whether others can join
  notes:[text]               - Optional: Additional notes
  friend_code:[code]         - Optional: HD2 friend code
  ping:[true/false]          - Optional: Whether to ping LFG role
  squad_name:[name]          - Optional: Create a temporary squad VC

/deploy standby              - Set your status to standby
  comms:[text]               - Optional: Comms preferences
  notes:[text]               - Optional: Additional notes
  ping:[true/false]          - Optional: Whether to ping LFG role

/deploy with                 - Deploy with a group
  with_users:[mentions]      - Users to deploy with
  faction:[faction]          - Optional: Enemy faction
  planet:[planet]            - Optional: Planet name
  difficulty:[1-10]          - Optional: Difficulty level
  open_deploy:[true/false]   - Optional: Whether others can join
  notes:[text]               - Optional: Additional notes
  ping:[true/false]          - Optional: Whether to ping LFG role

/deploy until [time]         - Set when your deployment expires
/deploy planet [planet]      - Update just your planet
/deploy faction [faction]    - Update just your faction
/deploy friendcode [code]    - Update just your friend code
/deploy notes [text]         - Update just your notes
/deploy difficulty [diff]    - Update just your difficulty
/deploy ping [true/false]    - Toggle LFG ping
/deploy privacy              - Toggle whether your deployment is open

/undeploy                    - Remove your deployment status
/status                      - Check your current status
/timeoutcheck                - Check deployment expiry
/setautodeploy [true/false]  - Configure auto-deployment
/squadvc [name]              - Create temporary squad voice channel
```

### Active Player Commands

```
/active                      - Show all active players
/sos                         - Toggle SOS mode for backup
/respond [user]              - Respond to an SOS call
/join [user]                 - Join another player's group
/timezone [zone]             - Set your timezone
```

### Equipment & Crafting

```
/equipment                   - View your crafted equipment
/liststratagems              - List all craftable stratagems
/booster                     - Activate a crafting booster
/showboosters                - View active boosters
```

### Attack System

```
/attack help                 - Show attack system help
/attackshow                  - Show/update current attack
/givesupplies                - Contribute to active attack
  supply:[name]              - Specific stratagem to give
  category:[type]            - OR category (offensive/defensive/support)
  quantity:[number]          - How many to give
```

### Medal Commands

```
/medal view [user]           - View yours or someone else's medals
/medal details [name] [user] - View details for a specific medal
/medal leaderboard           - Show medal leaderboard
```

### Miscellaneous Commands

```
/bulletins                   - Show all current dispatches
/orders view                 - View current order and progress
/stats show                  - Display server-wide stats
/roll [sides]                - Roll a random number
/sest                        - Show Super Earth Standard Time
/motivation                  - Get a motivational quote
/info                        - Show bot information
/help                        - Show all commands
```

## Admin Commands

### Server Setup

```
/setchannel [channel]        - Set channel for deployment status
/enablelfg [role]            - Set LFG ping role
/disablelfg                  - Remove LFG ping role
/setminigamechannel [channel]- Set channel for stratagem crafting
/setwelcomechannel [channel] - Set welcome message channel
/setvccategory [category]    - Set category for squad VCs
/setstatuscounters           - Configure voice channel counters
```

### Active List Management

```
/createactivelist            - Create persistent Active list
/deleteactivelist            - Delete all persistent Active lists
```

### Deployment Administration

```
/undeployuser [user] [reason]- Clear a user's deployment status
/silentundeployuser [user]   - Clear status without notification
```

### Order Administration

```
/orders create               - Create a new order
  title:[title]              - Short title for the order
  text:[description]         - Detailed order text
  until:[MM/DD HH:MM]        - When the order expires
  planets:[list]             - Optional: Target planets
  factions:[list]            - Optional: Target factions

/orders stats                - Update order statistics
/orders goals                - Set goals for order
/orders channel              - Set order channel
/orders clear                - Clear current order
/orders reset                - Reset order stats
```

### Medal Administration

```
/medal award                 - Award a medal to a user
  recipient:[user]           - User to award the medal to
  medal_type:[type]          - Type of medal
  medal_name:[name]          - Optional: Custom name
  emoji:[emoji]              - Optional: Medal emoji
  citation:[text]            - Optional: Reason for award

/medal remove                - Remove a medal from a user
/medal edit                  - Edit medal details
/listmedals                  - List all medals in the server
```

### Attack Administration

```
/attack create               - Start a new attack
  name:[name]                - Name for this attack
  req_offensive:[number]     - Required offensive supplies
  req_defensive:[number]     - Required defensive supplies
  req_support:[number]       - Required supportive supplies
  time_left:[time]           - When it expires (HH:MM or DD/MM HH:MM)
  description:[text]         - Optional: Extra details
  planet:[name]              - Optional: Planet name
  faction:[name]             - Optional: Attacking faction

/attack end [outcome]        - End the current attack
                               outcome: auto|success|failure
```

### Escape Pod & Minigame Administration

```
/spawnpod                    - Spawn an escape pod
  mode:[booster|items]       - Override pod contents
  booster_type:[type]        - Type of booster
  duration:[minutes]         - Booster duration
  items:[names]              - Comma-separated stratagem names
  quantity:[number]          - Quantity for each stratagem

/reset_equipment [user]      - Reset a user's equipment
```

### Stats Administration

```
/stats add                   - Add to server-wide stats
/stats reset                 - Reset server-wide stats
/listequipment               - Show total crafted equipment
```

### Moderation Commands

```
/execute                     - Ban a user with theatrical execution
  member:[user]              - Select a server member
  user_id:[id]               - Or paste a raw user ID
  reason:[text]              - Reason for execution

/executions                  - View the execution log
/censor                      - Mute a user with censorship citation
  member:[user]              - Select a server member
  user_id:[id]               - Or paste a raw user ID
  length:[HH:MM]             - Length of mute
  reason:[text]              - Reason for censorship

/censoredusers               - View all currently censored users
/exile                       - Kick a user with theatrical exile
/lockdown                    - Toggle 5-second slowmode in channel
```

## Troubleshooting

**Deployment Status Issues:**
- Make sure the bot has appropriate permissions in the status channel
- Check if the status channel is correctly set with `/setchannel`
- Try `/undeploy` and then re-deploy if your status seems stuck

**Stratagem Crafting Issues:**
- Ensure you're typing the exact stratagem pattern
- Check that you're in the designated minigame channel
- Crafting has a 1-minute cooldown per stratagem

**Squad VC Issues:**
- Verify that a VC category has been set with `/setvccategory`
- Ensure the bot has permission to create channels in that category
- You must be deployed or on standby to create a squad VC

**General Bot Issues:**
- Confirm the bot has all required permissions
- Check that the appropriate channels are configured

## Credits

- Bot developed by Vetaso & Gohan
- Special thanks to members of the Freedom Alliance and the '14th Ursine Corps'!
- Please do not use this bot for commercial services
- Helldivers 2 is owned by Arrowhead Game Studios and Sony Interactive Entertainment
- This bot is fan-made and not affiliated with the official game