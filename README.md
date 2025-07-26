# Gswarm Telegram Bot Setup Guide (Community Edition)

This guide will help you set up the **Gswarm Telegram Bot** to monitor your Swarm node and claim **The Swarm** Discord role.

---

## ✨ Step 1: Install Gswarm

### Install Go (Golang):
```bash
sudo rm -rf /usr/local/go
curl -L https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | sudo tar -xzf - -C /usr/local

# Add Go to PATH
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile
source ~/.bash_profile

go version
```

### Install Gswarm:
```bash
go install github.com/Deep-Commit/gswarm/cmd/gswarm@latest
```

---

## 🐞 Step 2: Create and Setup Telegram Bot

### 1. Create a Bot:
- Open Telegram and search **@BotFather**
- Send `/newbot`
- Choose a **name** and **username**
- Save the bot token

### 2. Get Your Chat ID:
- Start a chat with your bot and send any message
- In your browser, open:
```
https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates
```
- Find your `chat.id` in the response:
```json
"chat": {"id": 00000000}
```
- That number is your **ID**

---

## 🚀 Step 3: Run Gswarm Bot

```bash
screen -S gswarmbot
```

In your terminal, run:
```bash
gswarm
```
Follow the prompts and enter:
- Your **Bot Token**
- Your **ID**
- Your **EOA Address** EVM address (Login to [Gensyn Dashboard](https://dashboard.gensyn.ai) to find it)

---

## 🤝 Step 4: Link Discord and Telegram

### 1. Get Verification Code:
- Join the Discord server
- Go to **#⬛swarm-link** channel
- Type:
```bash
/link-telegram
```
- Copy the code you get

### 2. Verify the Code:
- In Telegram, type:
```bash
/verify <code>
```
(Replace `<code>` with your actual code)

Once verified, your Discord and Telegram will be linked, and you will earn **The Swarm** role!

---

## ✅ Tips
- Use `screen` to keep the bot running 24/7
- If `getUpdates` shows nothing, send a message to your bot and refresh

follow https://t.me/andhiiTGkamaii for more updates 
