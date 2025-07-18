
# 🐧 Linux `tar` Cheat Sheet — Archiving & Extracting `.log` Files

### 📁 Scenario:
You are working with log files located in `/var/log`, and you need to:

1. Archive the `.log` files into `log.tar`  
2. Store that archive in `~/archive`  
3. Extract those files into `~/backup`  
4. List and verify results — all without deleting anything

---

## 📌 Step-by-step Commands with Syntax Explanation

---

### 📂 1. Create folders in your home directory

```bash
mkdir ~/archive
mkdir ~/backup
```

🔍 **Explanation:**
- `mkdir` → Make directory (create a folder)
- `~` → Your home directory (e.g., `/home/sysadmin`)
- `~/archive` and `~/backup` → Target folders for storing the archive and extracted files

---

### 📂 2. Change into `/var/log`

```bash
cd /var/log
```

🔍 **Explanation:**
- `cd` → Change directory
- `/var/log` → Folder where system log files are stored
- This step avoids having to use `tar -C`

---

### 📦 3. Archive all `.log` files

```bash
tar -cvf ~/archive/log.tar *.log
```

🔍 **Explanation of flags:**

| Flag | Meaning |
|------|---------|
| `-c` | Create a new archive |
| `-v` | Verbose — list files as they are added |
| `-f` | File — name of the archive to create |
| `*.log` | Match all files ending in `.log` (only in the current directory) |

📁 The archive file `log.tar` is created in the `~/archive` folder and contains only filenames (no paths), like:

```
auth.log
dpkg.log
kern.log
...
```

---

### 🔍 4. List files inside the archive without extracting

```bash
tar -tvf ~/archive/log.tar
```

🔍 Explanation:

| Flag | Meaning |
|------|---------|
| `-t` | List contents of archive |
| `-v` | Verbose — show file details |
| `-f` | File — specify the archive file |

📋 You’ll see output like:

```
-rw-r--r-- sysadmin/sysadmin  ... auth.log
-rw-r--r-- sysadmin/sysadmin  ... dpkg.log
...
```

---

### 📥 5. Extract files into `~/backup`  
(📌 Option A: With `-C` flag)

```bash
tar -xvf ~/archive/log.tar -C ~/backup
```

🔍 Explanation:

| Flag | Meaning |
|------|---------|
| `-x` | Extract archive |
| `-v` | Verbose — show extracted files |
| `-f` | File — archive to extract |
| `-C` | Change to directory before extracting |

✅ Files will be extracted into the `backup` folder.

---

### 📥 5. Extract files into `~/backup`  
(📌 Option B: With `cd` — simpler for beginners)

```bash
cd ~/backup
tar -xvf ~/archive/log.tar
```

✅ Same result as above, but uses plain navigation (`cd`) instead of `-C`.

---

### ✅ 6. Check that files were extracted successfully

```bash
ls ~/backup
```

📋 Expected output:

```
alternatives.log  auth.log  bootstrap.log  cron.log  dpkg.log  kern.log  mail.log
```

---

### 📌 Important Notes

| 💡 Action | 🧠 What Happens |
|----------|----------------|
| `tar -cvf` | Creates archive — original files **stay where they are** |
| `tar -xvf` | Extracts files — archive remains **unchanged** |
| `*.log` | Matches only `.log` files — nothing else |
| `tar -tvf` | Lets you view what’s inside a `.tar` file without opening it |
| `-C` vs `cd` | Both can be used to control where files are extracted — pick what feels easier |

---

### 🧾 Final Command Set Recap

```bash
mkdir ~/archive
mkdir ~/backup
cd /var/log
tar -cvf ~/archive/log.tar *.log
tar -tvf ~/archive/log.tar
cd ~/backup
tar -xvf ~/archive/log.tar
ls ~/backup
```
