# Streams Sidebar
This is the documentation for NADotA's Twitch Stream Sidebar. Will mirror at a public repo once plugin reaches maturity, probably GitLab or Discourses's own Git.

## Intro
NADotA has a sidebar promoting streamers within the North American DotA community. This selection of streamers is stored in plaintext, and parsed to check against Twitch's Stream API.

We iterate through our own list upon refresh, digest the JSON callback, and put together a list of online streams as links with information pertaining to the stream title (Not always are the streamers playing the same game/competitive matchmaking) and viewercount.

This plugin, therefore, is highly dependent on Twitch's API.

## How it works

Using the front end of discourse we expose two text fields.  

1. `twitch_sidebar_title` - is the Block title of the widget. That is pretty straight forward.  Change the string to change the h2 of the wiget title.
2. `twitch_sidebar_user` - is a comma delimited text field.  Any admin can enter a twitch user name here.  ie.  Roragok, caseydota, tobiwan

We iterate through `twitch_sidebar_user` query them against twitch using [Get Stream by User](https://dev.twitch.tv/docs/v5/reference/streams/#get-stream-by-user).  We check if its live and grab each users viewer count.

If its live we add append it to the widget to display the User - viewers and link the entire div to the stream.


## Issues
Here is a list of known bugs. You can view current issues at the
[Issue Queue](https://git.roragok.com/NAMafiA/discourse-twitch-sidebar/issues)

#### CSS from parent plugin
[discourse-layouts](https://github.com/angusmcleod/discourse-layouts) adds a bunch of styling for some reason that really is unfortunate and breaks a lot of our styles.

#### Duplication of Streamers
Currently the plugin uses Jquery to append streamers to a div.  Instead of rebuilding the entire div, ember continues to run the jquery check for each user and continues to append.  This is most likely a bug due to my understanding of how to properly do ember/ruby.  I have a workaround that appends `channel_name` to the streamer div.

```js
 '<a class="streamer' + channel_name + '">target="_blank" href="https://twitch.tv/' + channel_name +'"><div class="streamer-wrapper clearfix"><div class="streamer-name">' + channel_name + '</div><div class="viewer-count">' + channel_viewers + '</div></div></a>'
 ```

 That way we can check if the div exists before adding it.  Probably super inefficient.

 ```js
   if(!$('a.streamer.'+channel_name).length)
  ```

  If it has a length that means it exists.

#### Sorting by Viewer Count
Currently the list displays the data in the list it is checked.  We need to store the data in an array to sort it by viewer count then display the data.
