# Discord Bot Cheat Sheet

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
