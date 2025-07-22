Good — you're installing **MongoDB 7.0** on **Ubuntu 22.04 (Jammy)**.

Here’s the **correct and updated** MongoDB 7.0 installation script with all official URLs and `apt-key` fix (for 2025 best practices):

---

### ✅ **Production-Ready MongoDB 7.0 Install Script (Ubuntu 22.04)**

```bash
# Step 1: Import MongoDB 7.0 GPG key and save to keyrings
curl -fsSL https://pgp.mongodb.com/server-7.0.asc | gpg --dearmor -o /usr/share/keyrings/mongodb-org-7.0.gpg

# Step 2: Add the MongoDB 7.0 repository for Ubuntu 22.04 (jammy)
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-org-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | \
  sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list

# Step 3: Update apt and install MongoDB 7.0
sudo apt update
sudo apt install -y mongodb-org

# Step 4: Enable and start MongoDB service
sudo systemctl enable mongod
sudo systemctl start mongod
```

---

### 📎 **Breakdown of URLs Used**

| Purpose             | URL                                                                    |
| ------------------- | ---------------------------------------------------------------------- |
| GPG Key (MongoDB 7) | `https://pgp.mongodb.com/server-7.0.asc`                               |
| APT Repo (Jammy)    | `https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse` |

---

### ✅ **Verify Installation**

```bash
mongod --version
sudo systemctl status mongod
```

---

### ⚠️ **Troubleshooting (Just in Case)**

If you see:

```bash
mongodb-org-database depends on mongodb-org-database-tools-extra
```

Fix it manually with:

```bash
sudo apt install mongodb-org-database-tools-extra
```

---

### 💾 Want it as `.sh` Script?

Would you like me to give you this in a ready-to-run `install-mongodb7.sh` file format too?
