# Discord Bot Cheat Sheet

## Initiate New Bot Project

1. Create folder 
2. ```cd``` into folder
3. ```npm init```
4. ```npm install discord.js```
5. Create main bot file (e.g. bot.js)

```sh
const Discord = require('discord.js');
const { Client, MessageEmbed } = require('discord.js');
const client = new Discord.Client();
const token = 'TOKEN-GOES-HERE';

client.login(token);

// Outputs message to console when bot sign ins
client.once('ready', () => {
    console.log('Bot is online')
});
```

6. Create [Application in Discord and Bot](https://discord.com/developers/applications)
7. Copy Token
8. Go to [this link](https://discordapi.com/permissions.html), set the permissions, add the ```Client ID``` and copy the link (this is the link for users to add the bot to Discord)
