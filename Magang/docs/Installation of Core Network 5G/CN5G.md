## Step 1: Setup for CN5G Pre-requisites
```
sudo apt install -y git net-tools putty

# https://docs.docker.com/engine/install/ubuntu/
sudo apt update
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Step 2: Configure OAI CN5G Files
**Get CN5G Zip File**
```
wget -O ~/oai-cn5g.zip https://gitlab.eurecom.fr/oai/openairinterface5g/-/archive/develop/openairinterface5g-develop.zip?path=doc/tutorial_resources/oai-cn5g
unzip ~/oai-cn5g.zip
mv ~/openairinterface5g-develop-doc-tutorial_resources-oai-cn5g/doc/tutorial_resources/oai-cn5g ~/oai-cn5g
rm -r ~/openairinterface5g-develop-doc-tutorial_resources-oai-cn5g ~/oai-cn5g.zip
```

## Step 3: Pull OAI CN5G Docker Images
```
cd ~/oai-cn5g
docker compose pull
```

## Step 4: Run OAI CN5G
**Start OAI CN5G**
```
cd ~/oai-cn5g
docker-compose up -d
```

**Stop OAI CN5G**
```
cd ~/oai-cn5g
docker-compose down
```

Continue to build gNB and NR-UE : [Here](https://github.com/bmw-ece-ntust/internship/blob/2025-TEEP-7-Filbert/docs/OAI%20gNB%20and%20%20NR-UE/Build%20gNB%20and%20NR-UE.md)

Reference :
https://gitlab.eurecom.fr/oai/openairinterface5g/-/blob/develop/doc/NR_SA_Tutorial_OAI_CN5G.md
