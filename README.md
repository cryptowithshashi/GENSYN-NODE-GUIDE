
# GENSYN TESTNET NODE GUIDE 

RL Swarm is an open source system for peer-to-peer reinforcement learning over the internet. Running a swarm node allows you to train your personal model against the swarm intelligence. Each swarm performs RL reasoning as a group, with a gossiping system (Hivemind) for collaborative improvement between models. You can also connect your node to the Gensyn Testnet, to receive an on-chain identity that tracks your progress over time.

RL Swarm is fully open and permissionless, meaning you can run it on a basic consumer laptop at home or on a powerful GPU in the cloud. You can also experiment with different models to see which ones perform best.






## REQUIREMENTS


Make sure your VPS meets the minimum requirements

## PRE REQUISITES

| Hardware | Requirements     |
| :-------- | :------- | 
| CPU | arm64 or amd64 architecture |
| RAM | Atleast 16 GM RAM |
| PYTHON VERSION | Version 3.10 or higher |
| GPU (OPTIONAL) | Supported models include RTX 3090, RTX 4090, A100, H100 |


## Install Dependencies
 - Update your system packages

```bash
  sudo apt-get update && sudo apt-get upgrade -y
```
- Install necessary tools like Python, pip, venv, Node.js, npm, yarn, git, curl, and screen

```bash
   sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl screen git yarn
```
- Python 3.10 venv
```bash
   sudo apt-get install python3 python3-pip
```   

```bash
   sudo apt install python3.10-venv
```   
- Then add Yarn’s repository and install it

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo     apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install -y yarn

```   
## Clone the RL-Swarm Repository

Clone the official Gensyn repository
```bash
  git clone https://github.com/gensyn-ai/rl-swarm.git
  cd rl-swarm

```
Run the Node in a Screen Session
```bash
  screen -S gensyn

```

## Set Up the Python Environment and Start the Node
- Inside the rl-swarm directory and within the screen session

```bash
   python3 -m venv .venv
```
- Activate the virtual environment

```bash
   source .venv/bin/activate
```

- Run the swarm script

```bash
   ./run_rl_swarm.sh
```   
## Login and Configuration

- The script will output logs and eventually display a message like Waiting for userData.json to be created... or provide a URL. 
- You need to access a login page, typically at `http://<Your_VPS_IP>:3000/`

## Accessing the Login Page from VPS

- If `http://<Your_VPS_IP>:3000/` doesn't work directly, you'll need to use SSH port forwarding (tunneling) from your local machine (not the VPS). Open a new terminal on your local computer and run.

```bash
   ssh -L 3000:localhost:3000 <your_vps_user>@<Your_VPS_IP> -p <Your_SSH_Port>
```
- (Replace placeholders with your VPS username, IP, and SSH port (usually 22))
- Enter your VPS password when prompted. Keep this SSH tunnel connection open.
- Now, open `http://localhost:3000/` in the browser on your local machine.

- Login: Use your preferred method (e.g., email) on the webpage.

## Monitor and Detach

- After successful login and configuration, the terminal on your VPS (inside the `screen` session) will show installation progress and eventually start the node activity. You might see your node's name appear in the logs.
- To detach from the screen session and let it run in the background, press `Ctrl+A`, then press `D`
- You can reconnect later using `screen -r gensyn` (or whatever you named it).


## Important Considerations:

- Backup: It's recommended to back up the `swarm.pem` file located in the `rl-swarm` directory after setup, as it contains your node's identity. 
- Troubleshooting VMs: If you encounter issues after disconnection or login problems, try stopping the script `Ctrl+C`, ensuring background processes are killed, deleting `swarm.pem` if re-logging in with a different account, and restarting the script.


For more information check out gensyn official github page -- [CLICK HERE](https://github.com/gensyn-ai)

By following these steps, you should have a running Gensyn Testnet Node on your VPS. Happy swarming!
## ABOUT ME

Twitter -- https://x.com/SHASHI522004

Github -- https://github.com/cryptowithshashi

