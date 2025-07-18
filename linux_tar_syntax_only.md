
# 📜 Linux Essentials — Archive & Extract Commands (Syntax Only)

This file contains the clean command list used in the archiving and extraction lab.

---

## 📁 Create Directories

```bash
mkdir ~/archive
mkdir ~/backup
```

## 📂 Change to `/var/log`

```bash
cd /var/log
```

## 📦 Archive `.log` Files

```bash
tar -cvf ~/archive/log.tar *.log
```

## 🔍 List Archive Contents

```bash
tar -tvf ~/archive/log.tar
```

## 📥 Extract Files into `~/backup` (Option A: with `cd`)

```bash
cd ~/backup
tar -xvf ~/archive/log.tar
```

## 📥 Extract Files into `~/backup` (Option B: using `-C`)

```bash
tar -xvf ~/archive/log.tar -C ~/backup
```

## ✅ Verify Files

```bash
ls ~/backup
```
