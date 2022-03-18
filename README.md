![add twitter API credentials](https://raw.githubusercontent.com/tainalo2/twitter-communication-tool-for-streamer/main/comm.png)
# twitter-communication-tool-for-streamer
A Node Red flow to update your name, profile picture, and banner when you go live. The banner is update regularly with a screenshot of your actual live.

# Summary
  - Prerequesites
  - Technical explanation
  - Installation
    - Twitch API registration
    - Twitter API registration
    - FNT file (and why Jimp is old)
    - Nodered (and the pleasure of just import the flow and enter your info)
    - How to custom it ?
  - Credit

# Prerequesites
  - A nodered server on 2.X or above (free low code GUI for NodeJS server) https://nodered.org/
  - The node-red-contrib-image-tools palette https://flows.nodered.org/node/node-red-contrib-image-tools

# Technical explanation
The objective is to update the twitter profile picture, name, and banner when you are streaming on your twitch channel
  - Every ten minutes nodered server asking to helix twitch API the stream status of your channel
  - If stream has change status, it's uploading a different profile picture and name to indicate your stream status
  - If status is LIVE, it's uploading a different banner with your actual twitch thumbnails (screen of your stream) and your game name

# Installation
 - Twitch API registration
   - Go to https://dev.twitch.tv/console/apps and login with your twitch account
   - Got to "Register an application", add a name to your application, and in "OAuth URL" write : "http://localhost"
   - For your application category chose "Other" and describe it (I have write : "An API to update my twitter PP by checking if I'm live")
   - Click "Create"
   - In your apllications list click "Manage"
   - Scroll down and save your "Client ID" and generate a User/Client Secret and save it too (NEVER SHARE IT !!!)

 - Twitter API registration
   - You need to ask access to API dashboard as developper to twitter (use this link : https://developer.twitter.com/en/docs/twitter-api/getting-started/getting-access-to-the-twitter-api). It's a long process like French Bureaucracy. But after you will have all access needed instantly !
   - Once you have acces to dashboard : https://developer.twitter.com/en/portal/dashboard
   - Go to : https://developer.twitter.com/en/portal/apps/new and name your app and create it
   - Go to : https://developer.twitter.com/en/portal/projects-and-apps , find your application and click on the key icon
   - Front of "API Key and Secret", click on "Regenerate", and  save your "API Key" and "API Secret Key" (NEVER SHARE IT !!!)
   - Front of "Access Token and Secret", click on "Regenerate", and  save your "Access Token" and "Access Token Secret" (NEVER SHARE IT !!!)
   - You are the best person in the world, be brave, never forget it, it's not a satanic incantation that will stop you !

 - FNT file (and why Jimp is old)
   - Jimp is a tool in JavaScript to manipulate images, it's the library in node-red-contrib-image-tools, and we want to use it to add some text on our banner (to see the game name). But ! It's a bit old and not support TTF font format and forced you to use FNT with already rendered files.
   - So in your nodered server you need to push files "OpanSansBold24Blanc.fnt" and "J0qnOXzPZqwthmJttZpfKjd3.ttf_0.png"
   - DON'T RENAME IT
   - Get the absolute directory of these files and save it for next step
 

 - Nodered (and the pleasure of just import the flow and complete it)
   - Copy the content of the git file : "nodered_flow1_1.json"
   - In nodered dashboard go to options and "Import"
   - Paste the file content and click "Import"
   - Go to https://github.com/n3odym3/Twitch-API_Node-RED to see how to copy your Twitch API information
   - In the new flow go to node "BASE64 and twitter name" and replace fourth first variables by your twitter API credentials
   ![add twitter API credentials](https://raw.githubusercontent.com/tainalo2/twitter-communication-tool-for-streamer/main/api_credentials.png)
   
   - Always in node "BASE64 and twitter name" replace your twitter name on and off stream
   - Always in node "BASE64 and twitter name" replace your twitter profile picture on and off stream. You need Base64 format without tag ! Take your PP (400x400 pixels) on this site and copy paste result : https://onlinepngtools.com/convert-png-to-base64
   ![add twitter API credentials](https://raw.githubusercontent.com/tainalo2/twitter-communication-tool-for-streamer/main/twitter_name_pp.png)
   
   - Always in node "BASE64 and twitter name" replace your FNT file path, the absolute directory to "OpanSansBold24Blanc.fnt"
   ![add twitter API credentials](https://raw.githubusercontent.com/tainalo2/twitter-communication-tool-for-streamer/main/fntPath.png)
   
   - Click "Done"
   - Click "Deploy"
   - Enjoy !

 - How to custom it ?
   - Actually you have my custom banner configured. You can change it by replacing flow.banner in node "BASE64 and twitter name"
   - Your banner need to be on 1500x500 pixels and a base64 format without tag ("data:image/png;base64,")
   - Position of stream capture is : x = 857, y = 71, for a resolution of 611x344
   - You can change those parameters in "open template SCREENSHOT" and "SCREEN Merge" nodes

# Credit
Create by tainalo2 : french streamer on twitch every week day from 07H to 09H (Paris hours)
All my links here : https://linktr.ee/tainalo2
Twitch Helix API flow by https://github.com/n3odym3
