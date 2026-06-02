# 🖥️ WSL — Accessing Windows Files from Kali

> After installing Kali Linux in [WSL](./README.md#wsl-2--kali-in-windows), here's how to access and troubleshoot Windows drive mounting.

---

## ✅ Access Windows Files

By default, WSL mounts your Windows drives under `/mnt`:

```bash
ls /mnt
# Output: c  d  e  wsl  wslg

cd /mnt/c/Users
ls
# Output: akash  'All Users'  Default  Public ...

cd /mnt/c/Users/akash/Desktop
```

---

## ⚠️ Drives Not Mounted? Fix It

### 1. Check what's mounted

```bash
ls /mnt
```

If you don't see `c`, `d`, etc. — drives aren't mounted.

---

### 2. Enable Automount

```bash
sudo nano /etc/wsl.conf
```

Add these lines:

```ini
[automount]
enabled = true
root = /mnt
```

Then restart WSL:

```bash
wsl --shutdown
```

Relaunch Kali.

---

### 3. Manual Mount (if automount fails)

```bash
sudo mount -t drvfs C: /mnt/c
cd /mnt/c/Users/akash/Desktop
```

---

### 4. Verify Windows Username

Check your actual username in `C:\Users\` from Windows File Explorer — it may differ from what you expect.

---

### 5. General Restart Fix

```bash
wsl --shutdown
wsl
```

---

## 📂 Navigate to Your Desktop

```bash
cd /mnt/c/Users
ls                          # find your username
cd /mnt/c/Users/akash/Desktop
ls                          # list desktop files
```

> 💡 Replace `akash` with your actual Windows username.

---

| ← [Back to All Commands](./README.md) | [File Permissions →](./permissions.md) |
| --- | --- |
