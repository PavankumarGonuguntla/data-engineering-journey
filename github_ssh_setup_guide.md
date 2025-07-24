# 🔐 GitHub SSH Setup: Main + Second Account (Step-by-Step)

This guide documents the complete process for setting up SSH access for one or more GitHub accounts.

---

## ✅ 1. Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Creates a new SSH key. `-C` is a label (usually your email).

### Optional for multiple accounts:
```bash
-f ~/.ssh/id_ed25519_main
```
Saves the key to a custom filename for easier identity separation.

---

## ✅ 2. List SSH Keys

```bash
ls -al ~/.ssh
```
Lists all existing SSH key files.

---

## ✅ 3. Show Public Key

```bash
cat ~/.ssh/id_ed25519_main.pub
```
Displays the public key to copy to GitHub.

---

## ✅ 4. Add Key to GitHub

Go to: https://github.com/settings/keys  
Paste your public key there.

---

## ✅ 5. Create SSH Config File

```bash
nano ~/.ssh/config
```

Paste this:

```bash
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_main
```

If you're using a second account:

```bash
Host github-second
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_second
```

---

## ✅ 6. Reset SSH Identities

```bash
ssh-add -D
```
Removes all loaded keys.

---

## ✅ 7. Load the Correct Key

```bash
ssh-add ~/.ssh/id_ed25519_main
```

---

## ✅ 8. Test SSH Connection

```bash
ssh -T git@github.com
```
Should respond:
```
Hi PavankumarGonuguntla! You've successfully authenticated...
```

---

## ✅ 9. Check Current Remote

```bash
git remote -v
```

---

## ✅ 10. Change Remote to SSH (if needed)

```bash
git remote set-url origin git@github.com:USERNAME/REPO.git
```

---

## ✅ 11. Push Your Code

```bash
git push
```

---

## ✅ Second GitHub Account Setup

- Create a second key: `id_ed25519_second`
- Add it to GitHub (second account)
- Add `Host github-second` in `~/.ssh/config`
- Clone like this:

```bash
git clone git@github-second:username/repo.git
```
