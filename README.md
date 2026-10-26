# Baileys — by ISMAIL MUGHAL

A lightweight WhatsApp Web API library for building WhatsApp bots. Connects directly over WebSocket — no browser needed.

## Requirements

- **Node.js 20 or newer**

## Install from GitHub

```bash
# npm (user/repo shorthand works)
npm install ismailmughal/baileys

# yarn (use the github: prefix — plain user/repo gives a 405 error)
yarn add github:ismailmughal/baileys
```

Or add it to your bot's `package.json`:

```json
"dependencies": {
  "@ismailmughal/baileys": "github:ismailmughal/baileys"
}
```

## Quick start

```js
const { default: makeWASocket, useMultiFileAuthState } = require('@ismailmughal/baileys')

async function start() {
    const { state, saveCreds } = await useMultiFileAuthState('auth_info')
    const sock = makeWASocket({ auth: state, printQRInTerminal: true })
    sock.ev.on('creds.update', saveCreds)
}

start()
```

Scan the QR code from WhatsApp **Linked Devices** on your phone. The session is saved in `auth_info/` so you only scan once.

> ⚠️ Use a spare/test number for bots. WhatsApp may ban numbers that use unofficial automation.
> Never share your `auth_info/` folder with anyone — whoever has it can control your WhatsApp.
