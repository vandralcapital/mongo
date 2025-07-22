# MongoDB 7.0 Offline Installation for Ubuntu 22.04.5

This repository contains `.deb` offline installation packages for **MongoDB 7.0.8** and **MongoSH 2.2.4**.

Use this to install MongoDB on any **Ubuntu 22.04.5 LTS server** without needing internet access during installation.

---

## 📦 Included Packages

* `mongodb-org-database_7.0.8_amd64.deb`
* `mongodb-org-server_7.0.8_amd64.deb`
* `mongodb-org-shell_7.0.8_amd64.deb`
* `mongodb-org-tools_7.0.8_amd64.deb`
* `mongodb-org-mongos_7.0.8_amd64.deb`
* `mongosh_2.2.4_amd64.deb`

---

## 🚀 Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/vandralcapital/mongo.git
cd mongo
```

---

### 2. Install the `.deb` Packages

```bash
sudo dpkg -i *.deb
```

If you encounter dependency errors:

```bash
sudo apt --fix-broken install -y
sudo dpkg -i *.deb
```

---

### 3. Start and Enable MongoDB

```bash
sudo systemctl start mongod
sudo systemctl enable mongod
```

---

### 4. Verify the Installation

```bash
mongod --version
mongosh
```

---

## 🔓 Optional: Enable Remote Access

Edit the config:

```bash
sudo nano /etc/mongod.conf
```

Change:

```yaml
bindIp: 127.0.0.1
```

To:

```yaml
bindIp: 0.0.0.0
```

Then:

```bash
sudo systemctl restart mongod
sudo ufw allow 27017
```

---

## 🔐 Optional: Create Admin User (if enabling auth)

```bash
mongosh
```

Inside the shell:

```js
use admin

db.createUser({
  user: "admin",
  pwd: "yourpassword",
  roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
})
```

---

## ✅ Done!

MongoDB 7.0.8 is now installed and ready to use offline.

---
