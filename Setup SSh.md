# Setting up SSH for GitHub

## 🛠️ Step 1: Check for Existing SSH Keys
```bash
ls -al ~/.ssh
```

## 🔑 Step 2: Generate a New SSH Key
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
- **`ssh-keygen`**: Tool to create a new SSH key.
- **`-t ed25519`**: Specifies the type of key to generate (Ed25519 is modern, secure, and fast).
- **`-C` "your_email@example.com"**: Adds a comment so you know which key is yours later (usually your GitHub email).

If `ed25519` gives errors, use this instead:
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
- **`-t rsa`**: RSA key type.
- **`-b 4096`**: Key strength (bits) – 4096 is secure.

## 🖥️ Step 3: Add SSH Key to SSH Agent
```bash
eval "$(ssh-agent -s)"
```
This starts the SSH agent.

```bash
ssh-add ~/.ssh/id_ed25519
```
This adds your private key (`id_ed25519`) to the agent.

## 🌐 Step 4: Add SSH Key to GitHub
```bash
cat ~/.ssh/id_ed25519.pub
```
This prints your public key.

➡️ Go to **GitHub → Settings → SSH and GPG keys → New SSH key** and paste the key.

## ✅ Step 5: Test SSH Connection to GitHub
```bash
ssh -T git@github.com
```
This tries to connect to GitHub using SSH.
- **`-T`**: Means "Don't start a shell session" (we're just testing authentication).



























