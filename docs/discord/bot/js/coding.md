# 開始寫程式

1. 新增 `index.js` 檔案在資料夾中

2. 輸入下列代碼 並將 機器人TOKEN 輸入進第行的 `""` 內
```js
const { Client, Intents } = require('discord.js');
const TOKEN = "" //輸入機器人TOKEN
const PREFIX = "t!" //修改為要的Prefix

const client = new Client({
  intents: [
    Intents.FLAGS.GUILDS,
    Intents.FLAGS.GUILD_MEMBERS,
    Intents.FLAGS.GUILD_BANS,
    Intents.FLAGS.GUILD_INTEGRATIONS,
    Intents.FLAGS.GUILD_WEBHOOKS,
    Intents.FLAGS.GUILD_INVITES,
    Intents.FLAGS.GUILD_VOICE_STATES,
    Intents.FLAGS.GUILD_PRESENCES,
    Intents.FLAGS.GUILD_MESSAGES,
    Intents.FLAGS.GUILD_MESSAGE_REACTIONS,
    Intents.FLAGS.GUILD_MESSAGE_TYPING,
    Intents.FLAGS.DIRECT_MESSAGES,
    Intents.FLAGS.DIRECT_MESSAGE_REACTIONS,
    Intents.FLAGS.DIRECT_MESSAGE_TYPING,
  ],
	partials: ['MESSAGE', 'CHANNEL', 'REACTION', "USER"],
	allowedMentions: { parse: ["roles", "users"], 
	repliedUser: false },
});


client.once('ready', () => {
	console.log('BOT READY');
});

client.on('messageCreate', (message) => {
	if (message.author.bot) {
		return;
	}
    if (!message.content.toLowerCase().startsWith(PREFIX)) {
        return;
    }
    if (message.author.bot || !message.content.toLowerCase().startsWith(PREFIX)) {
		return;
	}
    if (message.content === PREFIX + "ping") {
        message.replPy("Pong")
    }
});

client.login(TOKEN);
```