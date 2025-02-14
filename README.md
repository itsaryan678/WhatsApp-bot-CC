# 📖 CC PROJECTS WhatsApp Bot Documentation 🇵🇭 🇮🇩

This WhatsApp bot is built using **Baileys** and supports commands, events, message editing, replying, and template messages and more.

## 🔧 Features  

✅ Command-based system (Easily extendable)

✅ Event-driven actions (Automate responses)

✅ Permission levels (User, Admin, Owner)

✅ Cooldowns (Prevent spam)

✅ Command reloading (No need to restart)

✅ Message editing & replying

✅ Thumbnail previews & template messages

✅ Supports DM & Group chats

✅ Optimized logging system


## 📌 Getting Started  

### 1️⃣ Installation  

📌 Setup Guide

1️⃣ Install Dependencies

Make sure you have Node.js installed, then run:

npm install

2️⃣ Pairing the Bot

When you first run the bot, it will prompt you to enter a phone number and generate a QR code for pairing.

1. Start the bot:

node index.js


2. Scan the QR code using WhatsApp Web.


3. Once paired, the bot will remain connected until manually stopped or logged out.

### 2️⃣ Running the Bot  

```sh
node index.js  
```  
 
---

⚙️ Bot Configuration

The bot settings are stored in config.json:

{
    "owner": ["1234567890@s.whatsapp.net"],  
    "prefix": "/",  
    "botName": "MyBot"
}

owner → WhatsApp ID(s) of bot owner(s)

prefix → Prefix for commands (e.g., /)

botName → Name of the bot

---
## ⚙️ Command Structure  

Each command is a separate file in the **commands/** folder. A command typically looks like this:  

```js
module.exports = {  
    name: 'ping',  
    desc: 'Check bot latency',  
    cooldown: 5,  
    permission: 0,  
    dmUser: true,  
    run: async ({ sock, m }) => {  
        await sock.sendMessage(m.chat, { text: 'Pong! 🏓' }, { quoted: m });  
    }  
};  
```  

### 🏷️ Command Properties  

- `name` → Command trigger name.  
- `desc` → Description of the command.  
- `cooldown` → Time before the user can use the command again (in seconds).  
- `permission` → Required user level:  
  - `0` → Everyone  
  - `1` → Group Admins  
  - `2` → Bot Owner  
- `dmUser` → If `true`, allows usage in private chat.  
- `run()` → The function executed when the command is triggered.  

---  

## 🎭 Events  

Events are handled in the **events/** folder. Example:  

```js
module.exports = {  
    name: 'onJoin',  
    event: async ({ sock, m }) => {  
        await sock.sendMessage(m.chat, { text: `Welcome to the group, ${m.pushName}!` });  
    }  
};  
```  

---  

## 💬 Replying & Editing Messages  

### 🔁 Reply to a Message  

```js
await sock.sendMessage(m.chat, { text: 'Hello!' }, { quoted: m });  
```  

### ✏️ Edit a Sent Message  

```js
await sock.relayMessage(m.chat, {  
    key: m.key,  
    message: { conversation: 'Updated message text!' }  
}, {});  
```  

---  

## 🖼️ Sending Media & Template Messages  

### 🖼️ Sending an Image  

```js
await sock.sendMessage(m.chat, {  
    image: { url: 'https://example.com/image.jpg' },  
    caption: 'Here is an image!'  
}, { quoted: m });  
```  

### 🔗 Sending a Template with Thumbnail  

```js
await sock.sendMessage(m.chat, {  
    text: 'Check this out!',  
    contextInfo: {  
        externalAdReply: {  
            title: 'My Website',  
            body: 'Click to visit',  
            thumbnailUrl: 'https://example.com/thumb.jpg',  
            sourceUrl: 'https://example.com'  
        }  
    }  
});  
```  

---  
### Cooldowns (Prevent Spam)

Cooldowns limit how often a user can run a command.

cooldown: 10, // 10 seconds cooldown

If used too soon, the bot will reply:

You're using this command too fast. Wait 10s.

---
## 🔄 Reloading Commands  

If you modify a command file, you can reload it without restarting the bot:  

```js
global.cc.reloadCommand('ping');  
```  

---  

## 🚨 Error Handling  

Always wrap your async functions with try-catch to avoid bot crashes:  

```js
try {  
    await sock.sendMessage(m.chat, { text: 'Hello!' });  
} catch (err) {  
    console.error('Error:', err.message);  
}  
```  

---  

## 🎯 Conclusion  

This bot is designed for flexibility, allowing easy extension with new commands and events. Feel free to modify and improve it!. contact me if problem of bot https://www.facebook.com/cc.projects.jonell10 🚀  

## 🌟 Credits
 <h>Developers: Harold Hutchins? 🇵🇭 and ABN 🇮🇩<h>
 ## 👤 Dedication 
 <h>Rick GDPS Indo 🇮🇩 and You <h>