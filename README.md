### Github For Noobs


### What is Git?

Git is a tool that helps you **save different versions of your code**. Imagine writing a story and saving copies of every change — Git keeps track of all your changes so you can go back or share your work easily.

### What is GitHub?

GitHub is a **website (cloud service)** where you can **store your Git projects online**. It helps you share your code with others, work together, and keep your work safe.

---

### How do you connect your computer to GitHub?

There are **two ways** to connect:

1. **HTTPS (using URL and password or token)**
2. **SSH (using special keys)**

---

### What is HTTPS?

- You use a **web address (URL)** like `https://github.com/username/repo.git`.
- When you push or pull code, Git asks for your **username and password** (or a special Personal Access Token instead of password).
- It works everywhere, even on public computers.
- But you have to **type your password/token often**, which can be annoying.
- Also, passwords can be less secure if not handled carefully.

---

### What is SSH?

- SSH uses **special secret keys** to connect without typing your password every time.
- You create a **pair of keys** on your computer: one private (secret) and one public.
- You put the **public key on GitHub**.
- When you connect, GitHub checks your keys and lets you in without asking for a password.
- This is **more secure** and faster after setup.
- Ideal for your personal computer or laptop.

---

### Why is SSH preferred?

- **No need to enter passwords repeatedly**
- **More secure connection**
- Faster and smoother workflow
- Recommended for daily coding and teamwork

---

### Summary: HTTPS vs SSH

| Method    | Pros                                | Cons                                       |
| --------- | ----------------------------------- | ------------------------------------------ |
| **HTTPS** | Easy to start, works everywhere     | Requires password/token every time, slower |
| **SSH**   | Secure, no password prompts, faster | Needs one-time setup of keys               |

---
**As Using SSH is secure and faster for daily use definitely recommended for daily use and it is a little tricky to configure at first so will guide through it**

Now you’re ready to start! Follow the steps below to set up Git and connect to GitHub using SSH.

---

## Step 1 Create a GitHub Account


Go to [https://github.com](https://github.com) and sign up.

---

## ✅ Step 2: Download Git

Download Git for Windows:

[Download Git for Windows (64-bit)](https://github.com/git-for-windows/git/releases/download/v2.45.1.windows.1/Git-2.45.1-64-bit.exe)

---

## ✅ Step 3: Install Git and Open Git Bash

- Install the downloaded `.exe` file.
- After installation, search for **Git Bash** in your Start Menu and open it.

---

## ✅ Step 4: Configure Git (Set Username and Email)

These commands let Git know who you are: 
Put the Username and email same your Github account

```bash
git config --global user.name "SuperShekhar"
git config --global user.email "shekhargyawali138@gmail.com"
```

---

## ✅ Step 5: Generate SSH Key and Connect to GitHub

This connects Git on your machine to your GitHub account using SSH.

### 1. Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "shekhargyawali138@gmail.com"
```

Press click `Enter` key  three times to accept defaults.

### 2. Start the SSH agent

```bash
eval "$(ssh-agent -s)"
```

### 3. Add SSH key to the agent

```bash
ssh-add ~/.ssh/id_ed25519
```

### 4. Copy your SSH public key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the given output key.

### 5. Add the key to GitHub

- Open GitHub
- Go to **Settings > SSH and GPG keys**
- Click **"New SSH key"**
- Give it a title and paste your copied key
- Click **"Add SSH Key"**

---

## ✅ Step 6 : To Check if Connection is set and adding github to know host
In  git cli type
```bash
ssh -T git@github.com
```
- First time it will ask if you want to add github to add to know host
- type yes
- You should see a message like "Hi _your_username_! You've successfully authenticated, but GitHub does not provide shell access." This confirms your SSH connection is working.

## ✅ Step 7: Upload Your Local Project to GitHub

### 1. Create a New Repository

- Go to [https://github.com](https://github.com)
- Click **"New"**
- Give your repo a name and click **Create Repository**
- Afer that switch the option from https to ssh
- So copy the first block where it says  ... create a  new repository on the command line

### 2. Initialize Git in your local folder
	
- Go to your project folder on your file explorer which you want to upload in the created repo
- Shift + Right-click > Open Git Bash here

Then paste the code block the code block should seem like this


```bash
echo "# created_repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:supershekhar/created_repo.git
git push -u origin main
```


---

## ✅ Step 8: Confirm the Upload

- Refresh the GitHub tab in browser
- Your code should be visible in the repository
- Share the URL with others

> If the repository is private, only you and collaborators can view it

---

