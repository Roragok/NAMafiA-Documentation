# Streams Sidebar
This is the documentation for NADotA's Twitch Stream Sidebar. Will mirror at a public repo once plugin reaches maturity, probably GitLab or Discourses's own Git.

## INTRO
NADotA has a sidebar promoting streamers within the North American DotA community. This selection of streamers is stored in plaintext, probably RET/csv, and parsed to check against Twitch's "isOnline" Stream API.

We iterate through our own list upon refresh, digest the JSON callback, and put together a list of online streams as links with information pertaining to the stream title (Not always are the streamers playing the same game/competitive matchmaking) and viewercount. 

This plugin, therefore, is highly dependent on Twitch's API.

INCOMPLETE