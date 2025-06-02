
# GENSYN AI RL SWARM NODE GUIDE

RL Swarm is an open source system for peer-to-peer reinforcement learning over the internet. Running a swarm node allows you to train your personal model against the swarm intelligence. Each swarm performs RL reasoning as a group, with a gossiping system (Hivemind) for collaborative improvement between models. You can also connect your node to the Gensyn Testnet, to receive an on-chain identity that tracks your progress over time.

RL Swarm is fully open and permissionless, meaning you can run it on a basic consumer laptop at home or on a powerful GPU in the cloud. You can also experiment with different models to see which ones perform best.


## System Requirements

| Hardware | Requirements     |
| :-------- | :------- | 
| CPU | arm64 or amd64 architecture |
| RAM | Atleast 16 GM RAM |
| PYTHON VERSION | Version 3.10 or higher |
| GPU (OPTIONAL) | Supported models include RTX 3090, RTX 4090, A100, H100 |


  

## 🔧 Install Dependencies

Update system packages
```bash
sudo apt update && sudo apt upgrade -y
```

Install core tools: Python, pip, venv, curl, screen, git, lsof

```bash
sudo apt install -y python3 python3-venv python3-pip curl screen git lsof
```

Install Node.js 20.x and npm

```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -  
sudo apt install -y nodejs
```

Add Yarn repository and install Yarn

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -  
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list  
sudo apt update && sudo apt install -y yarn
```

Check versions (optional, verify installs)

```bash
python3 --version  
node -v  
npm -v  
yarn -v
```

## Clone and Setup RL-Swarm

Clone RL-Swarm repo

```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
```

Start a screen session for RL-Swarm

```bash
screen -S gensyn
```

Go to the project directory

```bash
cd rl-swarm
```

Create and activate Python virtual environment

```bash
python3 -m venv .venv  
source .venv/bin/activate
```

Install frontend dependencies (for modal-login)

```bash
cd modal-login  
yarn install  
yarn upgrade  
yarn add next@latest viem@latest
```

Go back to main directory and run the node

```bash
cd ..  
./run_rl_swarm.sh
```

## Login & Web Interface

After node starts, a web pop-up will appear. If not, open manually:

```bash
http://localhost:3000/
```

Login with your email → Enter OTP → Get your ORG_ID from terminal → Save it

### Hugging Face Prompt


- When asked Push models to Hugging Face? → Type `N`
- For W&B Integration → Type `3` for Don't visualize my results (or `1` if you want tracking)


### Manage Node & Screen Session

Detach from screen (keep node running)
Press `Ctrl + A`, then `D`

Re-attach to screen

```bash
screen -r gensyn
```

### Save `swarm.pem` file for future logins

Copy file from VPS to local machine:

```bash
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem ~/swarm.pem
```

## 🔄 Update to Latest Release (v0.4.3)

Access screen session

```bash
screen -r gensyn
```

Stop node (if running) Press `Ctrl+c`


Update repository

```bash
cd rl-swarm  
git switch main  
git reset --hard  
git clean -fd  
git pull origin main
```

Restart the node

```bash
./run_rl_swarm.sh
```

## ❓ FAQ

- What is swarm.pem?
→ It’s your key file for authenticating and managing your node. Keep it safe!

- Can I run this on Mac?
→ No. This guide is for Linux/WSL only.

- How do I check my node’s logs?
→ Re-attach to the screen session using `screen -r gensyn.`



For more information check out gensyn official github page -- [CLICK HERE](https://github.com/gensyn-ai)

By following these steps, you should have a running Gensyn Testnet Node on your VPS. Happy swarming!



## About Me

- **Twitter**: [https://x.com/SHASHI522004](https://x.com/SHASHI522004)
- **GitHub**: [https://github.com/cryptowithshashi](https://github.com/cryptowithshashi)
- **Telegram**: [https://t.me/crypto_with_shashi](https://t.me/crypto_with_shashi)
