# Database Schema

This is the proposed structure of how to store the data in a logical means.  I am new to this type of DB, but I want to store data so that it easily exportable.  The goal is to be able to get any of this data at [api.namafia.com](https://api.namafia.com)

## Mafia Game
This is the first table that will store the overall game data.  New entries for this table are created when a player runs the
`startgame` command.

- **game_id** - Number - This is the threadID of thread where the `startgame` command is invoked
- **game_start** - Number -This is the timestamp when `startgame` was invoked
- **game_end** - Number - This is the timestamp when `result` command was invoked
- **game_url** - String - URL of the thread where `startgame` was invoked
- **title** - String - Title of the thread where `startgame` was invoked
- **status** - Boolean - if the game is completed.
- **signed_players** - Map - This is a JSON object of signed players
- **host** - String - Username of the player who invoked `startgame` - not sure if we should be using user IDs.

## Mafia Day

This is the table that will store all the interactions on a day by day basis. The first day of every game will auto populate when the `startgame` command is invoked

- **parent_id** - Number - Reference to `game_id` of mafia-game table
- **day_id** - Number - threadID of the thread where `startday` is invoked.
- **day_url** - String - URL of the thread where `startday` is invoked
- **day_title** - String - Title of the thread where `startday` was invoked
- **day_start** - Number -This is the timestamp when `startday` was invoked
- **day_end** - Number - Should we add a `endday` command or timestamp when the next `startday` or result command is done?
- **votes** - Map - This is JSON map of player votes.
- **alive_players** - Map - This is JSON map of currently alive players in the game.


## Player

This table will store Player Data

- **user_id** - Number - User ID from discourse
- **user_name** - String - Current user name from discourse
- **wins** - Number - Number of Games Won
- **loses** - Number - Number of Games Lost

Nice to have player stat info if possible

- **town_games** - Number -Number of Town Games
- **town_wins** - Number - Number of Town Wins
- **town_loses** - Number - Number of Town Loses
- **mafia_games** - Number - Number of Mafia Games
- **mafia_wins** - Number - Number of Mafia Wins
- **mafia_loses** - Number - Number of Mafia Loses
- **third_games** - Number - Number of Third Wins
- **third_wins** - Number - Number of Third Wins
- **third_loses**  - Number - Number of Third Loses
