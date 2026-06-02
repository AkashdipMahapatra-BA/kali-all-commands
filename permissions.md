# 🔐 Linux File Permissions — Quick Reference

> ⚡ Quick help for everyday permission tasks.  
> 📘 Need a deep dive? → [**Linux File Permissions — Full Guide**](https://github.com/akashdip2001/linux-all-commands/blob/main/00%20Linux%20File%20Permission.md)

---

## List Files with Permissions

```bash
ls -la /mnt/c/Users/akash/Desktop
```

This shows: permissions · links · owner · group · size · date · name

---

## Understanding Permission Format

```
rwxr-xr-x
│││ │││ │││
│││ │││ └── Others: read + execute
│││ └───── Group:  read + execute
└──────── Owner:  read + write + execute
```

| Symbol | Meaning | Value |
|--------|---------|-------|
| `r` | Read | 4 |
| `w` | Write | 2 |
| `x` | Execute | 1 |
| `-` | None | 0 |

---

## Common Permission Combos

| Numeric | Symbolic | Use Case |
|---------|----------|----------|
| `777` | `rwxrwxrwx` | Full access for everyone (⚠️ use carefully) |
| `755` | `rwxr-xr-x` | Executable files & directories |
| `644` | `rw-r--r--` | Text/config files |
| `600` | `rw-------` | Private files (SSH keys, etc.) |
| `500` | `r-x------` | Read+execute for owner only |
| `000` | `---------` | No access at all |

---

## Quick Commands

```bash
# Full permissions for everyone
chmod 777 filename

# Standard directory permissions
chmod 755 /mnt/c/Users/akash/Desktop/*

# Standard file permissions
chmod 644 /mnt/c/Users/akash/Desktop/*

# Recursive — all directories to 755
find /path -type d -exec chmod 755 {} \;

# Recursive — all files to 644
find /path -type f -exec chmod 644 {} \;
```

---

## Change Ownership

```bash
# Change owner
sudo chown username filename

# Change owner + group
sudo chown username:groupname filename

# Recursive
sudo chown -R username:groupname /path/to/dir
```

---

> 📘 **Want to learn more?** Check the full detailed guide:  
> [Linux File Permissions — Complete Reference](https://github.com/akashdip2001/linux-all-commands/blob/main/00%20Linux%20File%20Permission.md)

---

| ← [Back to All Commands](./README.md) |
| --- |
