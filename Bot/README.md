# Discord Bot Template

This README explains how a basic Discord bot works and provides example code snippets to help you understand its functionality.

## How It Works

A Discord bot is a program that interacts with the Discord API to perform automated tasks in a Discord server. The bot listens for events (e.g., messages, reactions) and executes specific actions based on those events.

### Key Components

1. **Discord API Library**: A library like `discord.js` (JavaScript) is used to interact with the Discord API.
2. **Bot Token**: A unique token provided by Discord to authenticate the bot.
3. **Event Listeners**: Functions that respond to specific events, such as a new message or a user joining a server.
4. **Commands**: Predefined actions that the bot performs when triggered by specific keywords or prefixes.

---

## Example Code (JavaScript with `discord.js`)

### Installation

First, install the `discord.js` library:

```bash
npm install discord.js
```

### Basic Bot Example

Below is an example of a simple bot that responds to messages:

```javascript
const { Client, GatewayIntentBits } = require('discord.js');

// Create a new client instance
const client = new Client({ intents: [GatewayIntentBits.Guilds, GatewayIntentBits.GuildMessages, GatewayIntentBits.MessageContent] });

// Event listener for when the bot is ready
client.once('ready', () => {
    console.log(`Logged in as ${client.user.tag}`);
});

// Event listener for new messages
client.on('messageCreate', (message) => {
    // Ignore messages from the bot itself
    if (message.author.bot) return;

    // Read the content of a message
    if (message.content === 'hello') {
        message.channel.send('Hello! How can I assist you?');
    }
});

// Log in to Discord with your bot token
client.login('YOUR_BOT_TOKEN');
```

### Explanation

- `const client = new Client(...)`: Creates a new Discord client instance with specified intents.
- `client.once('ready', ...)`: Triggered when the bot successfully connects to Discord.
- `client.on('messageCreate', ...)`: Triggered whenever a new message is sent in a channel the bot has access to.
- `message.content`: Used to read the content of a message.
- `message.channel.send()`: Sends a message to the same channel.

Replace `'YOUR_BOT_TOKEN'` with your actual bot token from the Discord Developer Portal.

---
