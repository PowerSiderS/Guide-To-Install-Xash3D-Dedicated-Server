# Guide to Installing an Xash3D Dedicated Server (CS16Client on VPS)

This guide will show you how to create and host a **Xash3D Dedicated Server** for **CS16Client** using a VPS running Ubuntu.  
This README is designed for beginners and advanced users — just follow the steps carefully.

📺 **Watch the Full Tutorial on YouTube:** *[Your Link Here]*

---

## ⚠️ Before Asking for Help

- Make sure you **understand your issue**.  
- Ask **ChatGPT** or **DeepSeek** for help before saying “I have a problem” — most issues come from skipping steps or missing commands.
- Always **copy and paste** the commands exactly as written.

🔥 **And please — follow instructions carefully.**

---

## 📌 Requirements

### ✔ VPS Hosting
- Ubuntu **22.04 (64-bit)**
- Open ports (usually **27015**).  
  If your VPS provider blocks ports, ask AI or your provider how to open them.

### ✔ Android Users
- **JuiceSSH** (terminal): https://play.google.com/store/apps/details?id=com.sonelli.juicessh  
- **File Manager (FTP client)**: https://play.google.com/store/apps/details?id=com.alphainventor.filemanager

### ✔ PC Users
- **PuTTY** (SSH)
- **FileZilla** (FTP)

---

# 🚀 Start Installation

Open your SSH terminal and follow the steps carefully.

---

## **1. Enable i386 Architecture**
```
sudo dpkg --add-architecture i386
```

---

## **2. Update System and Install Aptitude**
```
sudo apt update && sudo apt upgrade -y
sudo apt install aptitude -y
```

---

## **3. Install Required Libraries**
```
sudo aptitude --without-recommends install \
git build-essential gcc-multilib g++-multilib \
libsdl2-dev:i386 libfreetype-dev:i386 libopus-dev:i386 \
libbz2-dev:i386 libvorbis-dev:i386 libopusfile-dev:i386 \
libogg-dev:i386
```

---

## **4. Install Wget, Unzip, Screen**
```
sudo apt install screen unzip wget -y
```

---

## **5. Go to /opt**
```
cd /opt
```

---

## **6. Download Xash3D Dedicated Server Template**
```
wget https://download1478.mediafire.com/j5lws4j75yegtynXu6WexZxcq1UaXtrt8JHl3ZQipFKRxpRoAUWcEDKhMPrMeeaThtmi4QzhwmBMp4SKr-xnFvBdHTjYzavV16K2Hl1FVQVE_tJ_qe21LIIS_UVLMCmU_8iM55Yub-Lv84NAZSxpzDsxvYB-da6VrwrEmgxOQgK_sQ/2emqul0tbd5zxp4/template_xash.zip \
&& unzip template_xash.zip \
&& rm template_xash.zip
```

Wait until it finishes.

---

## **7. Give Permission**
```
cd template_xash
chmod -R 777 xash
```

---

## **8. Configure `server.cfg`**
Use your FTP client to go to:

```
/opt/template_xash/cstrike/server.cfg
```

Edit:
- Server name  
- RCON password (optional)
- Other settings

---

# ⚡ FastDL Setup (Highly Recommended)

Open your `server.cfg` and set:

```
sv_downloadurl "http://YOUR_SERVER_IP/cstrike"
```

### Install Apache2 Web Server:
```
sudo apt-get install apache2 -y
```

### Create FastDL Directory:
Go to:

```
/var/www/html/
```

Create folder:
```
cstrike
```

Inside `cstrike`, upload:
- maps  
- models  
- sounds  
- sprites  
- any custom content

FastDL makes your server download files **10x faster**.

---

# 🟢 Run The Server

Inside `/opt/template_xash` run:

```
LD_LIBRARY_PATH=bin screen -S TEMPLATE_SERVER ./xash -game cstrike -port 27015 +map de_dust2 +maxplayers 32 +public 1
```

Your server is now running! 🎉  
To join it, open **CS16Client** on Android/PC — it will appear in the **Masterlist** if ports are open.

---

# 🧰 Useful Commands

### ✔ Reopen Server Screen
```
screen -r TEMPLATE_SERVER
```

### ✔ Stop Server (Inside screen)
Press:
```
CTRL + C
```

### ✔ Close Screen (Outside)
```
screen -S TEMPLATE_SERVER -X quit
```

---

# 🎉 Congratulations!

Your Xash3D Dedicated Server is now online!  
Remember to update **FastDL** whenever you add new maps or files to your server.

If you think something is missing, tell me in the video comments.

---

## • Enjoy & Have Fun! •