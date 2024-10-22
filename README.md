# Extension-nodes

Installing Chromium browser to run the extension depin nodes

---

# Join Crypto Console Community

Join TG : [Crypto Console Telegram](https://t.me/cryptoconsol) 

Follow X : [Crypto Console Twitter](https://www.x.com/cryptoconsol) 

Subscribe : [Crypto Console Youtube](https://www.youtube.com/@cryptoconsole)

---

## Hardware requirements:

| **Hardware** | **Minimum Requirement** |
|--------------|-------------------------|
| **CPU**      | 6 Cores                 |
| **RAM**      | 6 GB                    | 
| **Disk**     | 100  GB  SSD            |

---

# VPS Options

Credit Card/Paypal/Crypto credit card : 

VPS 1 : [Contabo: Cloud VPS 1](https://www.jdoqocy.com/click-101278318-15692486) 

VPS 2 : [Contabo: Cloud VPS 2](https://www.tkqlhce.com/click-101278318-13796472)

VPS 3 : [Contabo: Cloud VPS 3](https://www.dpbolvw.net/click-101278318-13796474)

VPS 4 : [Contabo: Cloud VPS 4](https://www.anrdoezrs.net/click-101278318-13796476)

---


Here’s an alternative method to install and run Chromium using Docker, based on the `lscr.io/linuxserver/chromium:latest` image:

### Step 1: Update VPS
```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt install curl -y
sudo apt install ca-certificates
```

### Step 2: Install Docker
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
docker version
```
### Step 2: Install docker compose
```
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)

curl -L "https://github.com/docker/compose/releases/download/"$VER"/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose
docker-compose --version
```


### Step 2: Pull the Chromium Docker Image
```bash
docker pull lscr.io/linuxserver/chromium:latest
```

### Step 3: Run Chromium in Docker
Run the following command to start Chromium with custom ports, time zone, and user credentials:
```bash
docker run -d \
  --name=chromium \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Europe/London \
  -e CUSTOM_USER=<username> \
  -e PASSWORD=<password> \
  -p 3000:3000 \
  -p 3001:3001 \
  --shm-size=1gb \
  -v /root/chromium/config:/config \
  --restart unless-stopped \
  lscr.io/linuxserver/chromium:latest
```

### Step 4: Access Chromium
In your browser, go to:
```bash
http://<VPS_IP>:3000
```

### Optional: Adjust Environment Variables
- **TZ**: Change the time zone as required.
- **Ports**: Modify ports if there are conflicts (e.g., `3000` and `3001`).

