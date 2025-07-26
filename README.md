# Gswarm Telegram Bot Setup Guide (Community Edition)

This guide will help you set up the **Gswarm Telegram Bot** to monitor your Swarm node and claim **The Swarm** Discord role.

---


### Step 1: Create a Bot
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

### now goto your gensyn node terminal and do all these simple task:

## ✨ Step 3: install nano

```bash
sudo apt install nano
```

### Step 4: make nano file
```bash
nano install_gswarm.sh
```

## 🐞 Step 5: paste script in nano 

```bash
#!/bin/bash
set -e

echo "=== Step 1: Installing Go 1.24.0 ==="
wget -q https://go.dev/dl/go1.24.0.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.24.0.linux-amd64.tar.gz
rm go1.24.0.linux-amd64.tar.gz

echo "=== Step 2: Setting Go PATH ==="
export PATH=$PATH:/usr/local/go/bin
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin

# Persist to bashrc
if ! grep -q "/usr/local/go/bin" ~/.bashrc; then
  echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
fi
if ! grep -q "$HOME/go/bin" ~/.bashrc; then
  echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.bashrc
fi

echo "=== Step 3: Verifying Go installation ==="
go version

echo "=== Step 4: Installing GSwarm via go install (Option 1) ==="
go install github.com/Deep-Commit/gswarm/cmd/gswarm@latest

if [ -f "$HOME/go/bin/gswarm" ]; then
  echo "=== Step 5: Moving gswarm binary to /usr/local/bin ==="
  sudo mv "$HOME/go/bin/gswarm" /usr/local/bin/gswarm
fi

echo "=== Step 6: Verifying gswarm installation ==="
gswarm --version || echo "❌ gswarm install failed via go install"

echo "=== Step 7: Also installing from source (Option 2) ==="
rm -rf "$HOME/gswarm"
git clone https://github.com/Deep-Commit/gswarm.git
cd gswarm
make build
sudo make install
cd ..
rm -rf gswarm

echo "=== Step 8: How to use GSwarm ==="
echo ""
echo "✅ To run the monitoring service:"
echo "    gswarm"
echo ""
echo "📦 To set up Telegram notifications:"
echo "    1. Get your Telegram bot token from @BotFather"
echo "    2. Get your Telegram chat ID (can be a user or group)"
echo "    3. Run gswarm with proper config or env vars"
echo ""
echo "🎉 Done!"
```

After paste the script → save (Ctrl+X, Y, Enter)

## 🐞 Step 6: make script excutable  

```bash
chmod +x install_gswarm.sh
./install_gswarm.sh
```

## 🐞 Step 7: after that just run

```bash
gswarm
```

Follow the prompts and enter:
- Your **Bot Token**
- Your **ID**
- Your **EOA Address** EVM address (Login to [Gensyn Dashboard](https://dashboard.gensyn.ai) to find it)

---

## 🤝 Step 8: Link Discord and Telegram

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
