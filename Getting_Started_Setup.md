# Getting Started: Git, GitHub, and Gradle

*Advanced Robotics — Intro to GitHub unit. Mac only.*

This doc gets your machine fully set up: a GitHub account, Git configured locally, your first
repository pushed, and the Gradle wrapper running a project. Day-to-day git commands (branching, pull
requests, merge conflicts, etc.) are covered in a separate reference doc — this one stops once
everything works and you've pushed one commit.

---

## 0. Before You Start

A few things to check or install before diving into GitHub itself.

### A quick terminal primer

You'll be using the Terminal (in VS Code: **Terminal → New Terminal**) for most of this. If you haven't
used a command line before, these three commands will get you through this doc:

| Command | What it does |
| --- | --- |
| `pwd` | Prints the folder you're currently in |
| `ls` | Lists the files/folders in your current folder |
| `cd folder-name` | Moves into `folder-name` (use `cd ..` to go back up one level) |

### Check whether Git is already installed

Open a terminal and run:

```bash
git --version
```

If Git isn't installed, macOS will prompt you to install the **Xcode Command Line Tools** — accept that
prompt and it'll install Git along with a few other developer tools. Run `git --version` again afterward
to confirm.

### Install Java (Eclipse Temurin JDK)

The Gradle wrapper needs a JDK on your machine (it downloads Gradle itself, but not Java).

1. Go to [adoptium.net/temurin/releases](https://adoptium.net/temurin/releases).
2. Pick the JDK version your teacher specifies for this project (a current LTS release, e.g. JDK 21, is a
   safe default if none is specified).
3. Select **macOS**, then the **.pkg** installer, then download it.
4. Open the downloaded `.pkg` and follow the installer prompts.
5. Confirm it worked:

```bash
java -version
```

---

## 1. Git vs. GitHub — and Getting Set Up on GitHub

**Git** is the version control tool that runs on your computer — it tracks changes to your files over
time. **GitHub** is a website/service built around Git — it hosts your repositories online and adds
collaboration features on top (pull requests, issues, etc.). You can use Git without GitHub, but for this
class we'll use them together.

### Create your GitHub account

- Official guide: [Creating an account on GitHub](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github)
- Use your **school email address**.
- **Don't use your real name as your username** — pick something you wouldn't mind being public, but that
  isn't personally identifying.

### Turn on two-factor authentication (2FA)

- Official guide: [Configuring two-factor authentication](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication)
- A TOTP authenticator app (e.g. Microsoft Authenticator, Google Authenticator) is recommended over SMS.
- **Save your recovery codes somewhere safe** — you'll need them if you lose access to your authenticator
  app.

---

## 2. Setting Up Git Locally

### Set your identity

Git attaches a name and email to every commit you make. Set this once, globally, so it's used for every
project on your machine:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_school_email@example.com"
```

Use the same email you used to sign up for GitHub, so your commits get linked to your GitHub profile.

### Generate an SSH key

SSH keys let you connect to GitHub securely without typing a password every time.

- Official guide: [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Background reading if you want it: [About SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh)

Broad strokes (follow the official guide above for the exact commands and prompts):

1. Generate a new key pair with `ssh-keygen`.
2. Start the ssh-agent and add your new key to it.

### Add your key to GitHub

- Official guide: [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- Copy your **public** key (the `.pub` file) — never share your private key.
- Paste it into GitHub under **Settings → SSH and GPG keys → New SSH key**.

### Test your connection

- Official guide: [Testing your SSH connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

```bash
ssh -T git@github.com
```

The first time, you'll be asked to confirm GitHub's host fingerprint — type `yes`. A successful test looks
like:

```
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

That message is what you want to see — it means it worked, even though it looks like an error at first
glance.

---

## 3. Creating Your First Repository

1. On GitHub, click **New repository**. Give it a name, and choose to initialize it with a README.
2. Clone it to your computer using the **SSH** URL (not HTTPS) — copy it from the green **Code** button on
   the repo page.

```bash
git clone git@github.com:your-username/your-repo-name.git
cd your-repo-name
```

3. Make a small change — for example, edit the README.
4. Stage, commit, and push your change:

```bash
git add .
git commit -m "Describe what you changed and why"
git push
```

5. Refresh the repository page on GitHub — your change should now be visible there.

---

## 4. Using the Gradle Wrapper

Projects for this class come with the **Gradle wrapper** already set up, so you won't need to install
Gradle yourself — the wrapper downloads the right version automatically the first time you use a command.

- Official docs: [Gradle Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html)

Run these from a terminal, inside the project's root folder (the one containing the `gradlew` file):

```bash
./gradlew build
```
Compiles your code and checks that everything's error-free.

```bash
./gradlew clean
```
Deletes previous build output — use this if something's behaving strangely and you want a fresh start.

```bash
./gradlew run
```
Compiles (if needed) and runs the project. This is the one you'll use most.

**If you get "permission denied"** when running `./gradlew`, make the script executable and try again:

```bash
chmod +x gradlew
```

---

## 5. You're All Set — Verification Checklist

- [ ] `git --version` works
- [ ] `java -version` works
- [ ] Git identity configured (`git config --global user.name` / `user.email`)
- [ ] GitHub account created with school email, 2FA enabled, recovery codes saved
- [ ] SSH key generated, added to GitHub, `ssh -T git@github.com` succeeds
- [ ] Created a repository, cloned it, made a commit, and pushed it successfully
- [ ] `./gradlew run` works on a sample project without errors

If every box is checked, you're ready for the rest of the Intro to GitHub unit.
