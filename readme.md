# HD2 Utility Bot - Comprehensive Documentation

Welcome to the HD2 Utility Bot documentation! This Discord bot provides a comprehensive suite of features to enhance your Helldivers 2 server experience, including deployment tracking, stratagem crafting, attack coordination, medal systems, and more.

## Table of Contents

1. [Overview](#overview)
2. [Getting Started](#getting-started)
3. [User Commands](#user-commands)
   - [Deployment System](#deployment-system)
   - [Stratagem Crafting & Minigames](#stratagem-crafting--minigames)
   - [Medals](#medals)
   - [Player Cards](#player-cards)
   - [War Orders](#war-orders)
   - [Statistics](#statistics)
   - [Fun & Miscellaneous](#fun--miscellaneous)
4. [Administrator Commands](#administrator-commands)
   - [Server Setup](#server-setup)
   - [Moderation Tools](#moderation-tools)
   - [Attack System Management](#attack-system-management)
   - [Order Management](#order-management)
   - [Medal Management](#medal-management)
   - [Statistics Management](#statistics-management)
   - [Bulletin Management](#bulletin-management)
5. [Support](#support)

## Overview

HD2 Utility Bot is designed to enhance your Helldivers 2 Discord server with a complete suite of immersive, themed features that tie into the game's unique style and atmosphere. From tracking who's playing to organizing complex group activities, this bot creates a more cohesive community experience.

## Getting Started

To get started with the bot:

1. **Administrators**: Set up your server using the `/setchannel` command to designate where deployment status messages will appear
2. **Users**: Use `/deploy me` to set your current gameplay status
3. **Everyone**: Check `/active` to see who's currently playing
4. **Crafting**: Set a minigame channel with `/setminigamechannel` where users can craft stratagems
5. **Help**: Use `/help` for a complete list of user commands and `/adminhelp` for administrative commands

## User Commands

### Deployment System

The deployment system allows players to share their current status, form groups, and coordinate gameplay.

#### Basic Deployment

| Command | Description |
|---------|-------------|
| `/deploy me` | Set your status to deployed with optional parameters (faction, planet, difficulty, etc.) |
| `/deploy standby` | Mark yourself as available to join others (LFG status) |
| `/deploy with` | Update your deployment group without changing other details |
| `/undeploy` | Remove your deployment status |
| `/status` | Check your current deployment status |
| `/active` | View all currently deployed/standby players |
| `/timeoutcheck` | Check how long until your deployment expires |

#### Status Field Editing

| Command | Description |
|---------|-------------|
| `/deploy planet` | Update just your planet field |
| `/deploy faction` | Update just your faction field |
| `/deploy friendcode` | Update just your HD2 friend code |
| `/deploy notes` | Update just your deployment notes |
| `/deploy difficulty` | Update just your difficulty setting |
| `/deploy grinding` | Toggle grinding status for resources |
| `/deploy ping` | Toggle LFG role ping |
| `/deploy until` | Change your automatic undeploy time (24HR format) |
| `/deploy privacy` | Toggle whether others can join your lobby |

#### Group Management

| Command | Description |
|---------|-------------|
| `/join` | Join another user's deployment group |
| `/respond` | Respond to an SOS call |
| `/sos` | Toggle SOS mode for urgent backup |
| `/setgroupname` | Give your current squad a custom name |
| `/squadvc` | Create a temporary squad voice channel |

#### Configuration

| Command | Description |
|---------|-------------|
| `/timezone` | Set your timezone for time-based commands |
| `/setautodeploy` | Enable/disable automatic deployment when Discord detects you're playing |
| `/setlfgpref` | Configure whether to ping LFG role by default |

### Stratagem Crafting & Minigames

The minigame system includes stratagem crafting, attack coordination, and escape pod events.

#### Stratagem Crafting

To craft stratagems, simply type their directional input sequence (e.g., `⬇️⬆️⬅️➡️`) in the designated minigame channel.

| Command | Description |
|---------|-------------|
| `/equipment` | View your crafted equipment, or someone else's |
| `/liststratagems` | List all craftable stratagems and their input sequences |
| `/booster` | Activate a crafting booster from your inventory |
| `/showboosters` | Show active boosters and their remaining time |

#### Attack System

| Command | Description |
|---------|-------------|
| `/attack help` | Show help for the attack minigame |
| `/attackshow` | Display the current attack and its progress |
| `/givesupplies` | Contribute crafted supplies to the active attack |

#### Escape Pods

Escape pods randomly appear in the minigame channel. Type **SALUTE** to claim their contents when they appear.

### Medals

Track achievements and awards with the medal system.

| Command | Description |
|---------|-------------|
| `/medal` | View your medals |
| `/medal view` | View someone else's medals |
| `/medal details` | View details for a specific medal |
| `/medal leaderboard` | Show the server's medal leaderboard |

### Player Cards

Create and customize your Helldiver profile card.

| Command | Description |
|---------|-------------|
| `/helldiverinfo create` | Create or update your Helldiver info card |
| `/helldiverinfo show` | Display your info card or someone else's |
| `/helldiverinfo set-rank-icon` | Set a rank icon for your player card |
| `/helldiverinfo set-special-icon` | Set a special icon for your player card |
| `/helldiverinfo set-title` | Update your Helldiver title |
| `/helldiverinfo set-enlistment` | Update your enlistment date |
| `/helldiverinfo set-homeworld` | Set your Helldiver's home planet |
| `/helldiverinfo set-quote` | Update your player card quote |
| `/helldiverinfo set-stratagem` | Set your favorite non-support stratagem |
| `/helldiverinfo set-support` | Set your favorite support weapon |

### War Orders

Track server-wide objectives and progress.

| Command | Description |
|---------|-------------|
| `/orders` | View the current war order |
| `/orders view` | Display detailed order progress and objectives |

### Statistics

| Command | Description |
|---------|-------------|
| `/stats show` | Display server-wide statistics |

### Fun & Miscellaneous

| Command | Description |
|---------|-------------|
| `/roll` | Roll a random number (default: d20, can specify sides) |
| `/sest` | Show current Super Earth Standard Time |
| `/motivation` | Get a motivational quote from the Democracy Officer |
| `/dissident` | Report someone to the Ministry of Unity (fun roleplay) |
| `/dissidentscore` | Check how many times a user has been reported |
| `/dissidentleaderboard` | Show the users with the most dissident reports |
| `/info` | Display bot information and help |
| `/help` | Show all available commands |
| `/bulletins` | Show all current dispatches from approved guilds |

## Administrator Commands

### Server Setup

| Command | Description |
|---------|-------------|
| `/setchannel` | Set the channel for deployment status messages |
| `/setminigamechannel` | Set the channel for stratagem crafting |
| `/enablelfg` | Set a role to ping for LFG notifications |
| `/disablelfg` | Remove LFG role ping setting |
| `/enablegrindrole` | Set role to ping for grinding notifications |
| `/disablegrindrole` | Remove grinding role ping setting |
| `/setwelcomechannel` | Set and enable the channel for welcome messages |
| `/setvccategory` | Set the category where temporary squad VCs will be created |
| `/setstatuscounters` | Configure voice channels to display deployment counts |
| `/adminhelp` | Show admin-only commands |

### Moderation Tools

These commands are styled to fit the Helldivers theme:

| Command | Description |
|---------|-------------|
| `/execute` | Ban a user with a theatrical "execution" message |
| `/executions` | View the execution log (ban history) |
| `/censor` | Mute (timeout) a user with a "censorship citation" |
| `/censoredusers` | View all currently censored (muted) users |
| `/exile` | Kick a user with an "exile order" |
| `/lockdown` | Toggle a 5-second slowmode "comms lockdown" in the channel |
| `/surveillancereport` | Display the server's audit log |
| `/undeployuser` | Clear another member's deployment status |
| `/silentundeployuser` | Clear a user's status without notification |
| `/cleardissidentscore` | Reset a user's dissident report count |
| `/birthday` | Send an overdramatic birthday greeting to a user |

### Active List Management

| Command | Description |
|---------|-------------|
| `/createactivelist` | Create a persistent Active list in the current channel |
| `/deleteactivelist` | Delete all persistent Active lists in this guild |

### Attack System Management

| Command | Description |
|---------|-------------|
| `/attack create` | Start a new attack (with supplies needed, time limit, etc.) |
| `/attack end` | End the current attack |
| `/spawnpod` | Manually spawn an escape pod in the minigame channel |
| `/reset_equipment` | Reset a user's equipment counts |

### Order Management

| Command | Description |
|---------|-------------|
| `/orders create` | Create a new war order |
| `/orders stats` | Update order statistics |
| `/orders goals` | Set goals for the current order |
| `/orders channel` | Set the order notification channel |
| `/orders clear` | Clear the current order |
| `/orders reset` | Reset order statistics without removing the order |

### Medal Management

| Command | Description |
|---------|-------------|
| `/medal award` | Award a medal to a user |
| `/medal remove` | Remove a medal from a user |
| `/medal edit` | Edit medal details |
| `/listmedals` | List every medal in the server and its owner |

### Statistics Management

| Command | Description |
|---------|-------------|
| `/stats add` | Add to server-wide statistics |
| `/stats reset` | Reset all server-wide statistics |
| `/listequipment` | Show total crafted equipment counts for this server |

### Bulletin Management

For approved guilds only:

| Command | Description |
|---------|-------------|
| `/bulletin` | Post a dispatch bulletin |
| `/clearbulletin` | Clear your guild's dispatch bulletin |
| `/clearbulletinchannels` | Remove this channel from bulletin tracking |

## Support

- **Support Server**: Join our support server at https://discord.gg/Qfdn4rWAt2
- **Clan Leaders**: Interested in getting your clan added to the bulletin system and your logo added to your playcard? Contact Vetaso (thexant) in the support server.

---

*Bot created by Vetaso & Gohan. Special thanks to members of the Freedom Alliance and specifically, '14th Ursine Corps'!*
