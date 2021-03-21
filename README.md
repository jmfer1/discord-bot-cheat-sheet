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

### Code commands in separate files

For bots with several commands, it is recommended to code each command on a separate .js file. For this to work, create a folder ```commands``` in the bot directory

```sh
// Get into other JS files
const fs = require('fs');

// Create a collection to have all commands stored
client.commands = new Discord.Collection();

//Make sure all files we are reading are JS files
const commandFiles = fs.readdirSync('./commands/').filter(file => file.endsWith('.js'));

//Create a for loop to loop through all files and make sure it is getting the correct file
for(const file of commandFiles){
    const command = require(`./commands/${file}`);
    client.commands.set(command.name, command);
}
```
