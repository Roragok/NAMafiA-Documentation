# MafiaBot

This is to discuss thecommands  of the Mafia MafiaBot.
The MafiaBot is using [HuBot](https://hubot.github.com/) and the [Discourse Adapater](https://www.npmjs.com/package/hubot-discourse-adapter).

## Commands

Below are the proposed list of commands broken into two sections.  Host and Player

#### Required Commands
Player

- **lynch** - Usage `@mafiabot lynch example` - This command will record your lynch target.
- **unlynch** - Usage `@mafiabot unlynch` - This command will clear your current lynch.

Host

- **startgame** - Usage `@mafiabot startgame @playerNames` - playerNames are space delimited list of signed players
- **startday** - Usage `@mafiabot startday parentThreadID` - This will start the next day and associate the thread with the parent thread.  You can find the parent thread id in the url of the first game `https://namafia.com/t/threadname/threadID`
- **add** - Usage `@mafiabot add @playername` - Adds a player to a list of signed players incase a name was missed.
- **remove** - Usage `@mafiabot remove @playername` - Removes a player from the list of signed players incase of a mistake.
- **sub** - Usage `@mafiabot sub @playerSubIn @playerSubOut` - Subs a player into the game by adding the new player to the list and removing the old player
- **kill** - Usage `@mafiabot kill @playerNames` - playerNames are a space delimited list of players killed

Both :

- **votecount** - Usage `@mafiabot votecount` - This command will output the current vote count of the day.  Alias `@mafiabot vc`

#### Nice to Have Commands

Player:

- **stat** - Usage `@mafiabot stat [@playerName]` - playerName is an optional command.  It will lookup the person who issued the command unless a target is specified.  Will reply in a PM to whoever issued the command to avoid people being obnoxious.
- **alive** - Usage `@mafiabot alive` - This will return to the game thread the list of currently alive players.

Host:

- **zeus** - Usage `@mafiabot zeus @playername` - emulates the kill command but with Zeus Flair.
- **result** - Usage `@mafiabot result winningTeam @playerNames` - where WinningTeam is either (Town, Mafia, Third), playerNames are space delimited list of winning players
