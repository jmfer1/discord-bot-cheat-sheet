# Discord Bot Cheat Sheet

## Initiate New Bot Project

1. Create folder 
2. ```sh cd``` into folder
3. ```sh npm install discord.js```
4. ```sh npm init```
5. Create main bot file (e.g. bot.js)

```sh
const Discord = require('discord.js');
const { Client, MessageEmbed } = require('discord.js');
const client = new Discord.Client();
const token = 'TOKEN-GOES-HERE';

client.login(token);

// Outputs message to console when bot sign ins
client.once('ready', () => {
    console.log('Support Bot is online')
});
```
