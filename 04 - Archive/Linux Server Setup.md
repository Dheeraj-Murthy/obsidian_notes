Perfect! Since you don’t need remote access (like from outside your local network), we’ll set up a **NAS + Docker-based server** that works **entirely over your local Wi-Fi** — all devices on the same network will be able to:

- Access shared files (NAS)
    
- Use self-hosted apps (via Docker)
    
- Let you keep using your GUI (Hyprland) as usual
    
- Optionally SSH from other devices on LAN
    

---

## **⚙️ LET’S SET UP YOUR ARCH LINUX SERVER (With GUI + NAS + Docker)**

---

### **✅ STEP 1:** 

### **System Update + Essentials**

  

Open a terminal and run:

```
sudo pacman -Syu
sudo pacman -S docker docker-compose samba nfs-utils rsync openssh
```

Enable required services:

```
sudo systemctl enable --now docker
sudo systemctl enable --now sshd
```

> 📝 This gives you:

- > Docker & Compose for containers
    
- > Samba & NFS for file sharing
    
- > rsync for backups
    
- > SSH for remote LAN access (optional)
    

---

### **✅ STEP 2:** 

### **Create a Shared Folder**

  

Let’s create a folder that will be shared on the network.

```
sudo mkdir -p /srv/public
sudo chown -R nobody:nobody /srv/public
sudo chmod -R 0777 /srv/public
```

---

### **✅ STEP 3:** 

### **Configure Samba (For Windows, macOS, Linux access)**

  

Edit the config:

```
sudo nano /etc/samba/smb.conf
```

At the end of the file, add:

```
[Public]
  path = /srv/public
  browseable = yes
  writable = yes
  guest ok = yes
  create mask = 0666
  directory mask = 0777
```

Then enable Samba:

```
sudo systemctl enable --now smb nmb
```

> 🔎 Access from other devices:

- > Windows: \\<your-laptop-ip>\Public
    
- > macOS: ```````````
    
- > Linux: smb://<your-laptop-ip>/Public or mount via file manager
    

  

Get your local IP:

```
ip a | grep inet
```

Look for something like 192.168.x.x (that’s your NAS address).

---

### **✅ STEP 4:** 

### **(Optional) Set Up NFS for Linux Machines**

  

Add export rule:

```
sudo nano /etc/exports
```

Add:

```
/srv/public *(rw,sync,no_subtree_check)
```

Apply and enable:

```
sudo exportfs -a
sudo systemctl enable --now nfs-server
```

---

### **✅ STEP 5:** 

### **Run Self-Hosted Apps via Docker**

  

Create a folder for your Docker stack:

```
mkdir -p ~/selfhost
cd ~/selfhost
```

Create docker-compose.yml:

```
nano docker-compose.yml
```

Paste this:

```
version: '3.8'

services:
  portainer:
    image: portainer/portainer-ce
    ports:
      - "9000:9000"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data:/data
    restart: unless-stopped

  jellyfin:
    image: jellyfin/jellyfin
    ports:
      - "8096:8096"
    volumes:
      - /srv/public/media:/media
      - jellyfin_config:/config
    restart: unless-stopped

volumes:
  portainer_data:
  jellyfin_config:
```

Then run:

```
docker-compose up -d
```

> ✅ Now you’ve got:

- > **Portainer**: access at http://<your-ip>:9000 (Docker management UI)
    
- > **Jellyfin**: access at http://<your-ip>:8096 (media server)
    
- > Media folder linked to /srv/public/media on your NAS
    

---

### **✅ STEP 6:** 

### **Access from Other Devices (Same Wi-Fi)**

  

On any device connected to the same Wi-Fi:

- **Jellyfin**: http://192.168.x.x:8096
    
- **Portainer**: http://192.168.x.x:9000
    
- **File Share**: smb://192.168.x.x/Public or \\192.168.x.x\Public
    

  

Replace 192.168.x.x with your laptop’s LAN IP.

---

### **✅ STEP 7:** 

### **Optional Tools for Development**

  

Install developer tools:

```
sudo pacman -S neovim tmux lazygit zsh ripgrep nodejs go rustup
rustup default stable
```

You can now use your server for:

- Code projects
    
- Hosting dev databases in Docker
    
- Git operations via LAN
    

---

## **✅ Final Result**

  

You’ve now got:

- ✅ Full GUI access via Hyprland
    
- ✅ Local NAS file sharing for your LAN
    
- ✅ Self-hosted apps running on Docker
    
- ✅ Developer tooling for coding and experimenting
    

---

Want a script to automate all of this? Or want to add specific services (like Gitea, Nextcloud, MinIO, etc.)?