# Guide to Installing an Xash3D Dedicated Server (CS16Client on VPS)

This guide will show you how to create and host a **Xash3D Dedicated Server** for **CS16Client** using a VPS running Ubuntu.  
This README is designed for beginners and advanced users — just follow the steps carefully.

📺 **Watch the Full Tutorial on YouTube [here!](https://youtu.be/lVroJeo5VMA)** 

👉 **How to install Mods to your server**
[Watch Here!](https://youtu.be/W6Cdvp6ASFg?si=IlbrND7NYdJ9fEcY)
---

## ⚠️ Before Asking for Help

- Make sure you **understand your issue**.  
- Ask **ChatGPT** or **DeepSeek** for help before saying “I have a problem” — most issues come from skipping steps or missing commands.
- Always **copy and paste** the commands exactly as written.

- **And please — follow instructions carefully. Don't be a RETARD!**

---

## 📌 Requirements

### ✔ VPS Hosting
- Ubuntu **22.04 (64-bit)**
- Open ports (usually **27015**).  
  If your VPS provider blocks ports, ask AI or your provider how to open them.

### ✔ Android Users
- **JuiceSSH** (terminal): [Download From Here](https://play.google.com/store/apps/details?id=com.sonelli.juicessh)
- **File Manager (FTP client)**: [Download From Here](https://play.google.com/store/apps/details?id=com.alphainventor.filemanager)

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

## **2. Install Aptitude**
```
sudo apt install aptitude -y
```

---

## **3. Install Required Libraries**
```
sudo aptitude --without-recommends install git build-essential gcc-multilib g++-multilib libsdl2-dev:i386 libfreetype-dev:i386 libopus-dev:i386 libbz2-dev:i386 libvorbis-dev:i386 libopusfile-dev:i386 libogg-dev:i386 -y
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

Go To: ```https://www.mediafire.com/file/2emqul0tbd5zxp4/template_xash.zip/file```

Then Keep pressing on the blue rectangle and select **Copy Link Address**

Note: if you opened link from android. make sure to select Desktop site before copy!!

then back to terminal and write

```
wget <link you copied> && unzip template_xash.zip && rm template_xash.zip
```

Wait until it finishes.

**Optional**: you can download template in your device then upload zip file by FTP App

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