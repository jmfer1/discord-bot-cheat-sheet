# Discord Bot Cheat Sheet

### Initiate New Bot Project

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
9. ```node .``` to run the bot

### Bot Prefix

Add the following line to the main bot code to configure a prefix to call the bot (e.g. "!" or "-")

```sh
const prefix = "!"

// Break the code if the message does not start with the prefix or if message author is the bot
client.on('message', message =>{
    if(!message.content.startswith(prefix) || message.author.bot) return;
});
```

### Ping Pong Sample Command

```sh
client.on('message', message => {

    if(message.content.toLowerCase() === 'ping')
        message.channel.send('pong!');
```

### Splice (Split and Slice)

Splice allows users to use commands such as ```!check wiki```

```sh
const args = message.content.slice(prefix.length).split(/ +/);
const command = args.shift().toLowerCase();
```

Use case example:

```sh
client.on('message', message =>{
    if(!message.content.startswith(prefix) || message.author.bot) return;
   
   const args = message.content.slice(prefix.length).split(/ +/);
   const command = args.shift().toLowerCase();

});
```
