Here is the updated `README.md` with enhanced clarity on generating secondary account tokens and required permissions. I've added a dedicated subsection that details the exact scopes needed and the collaborator invitation process, ensuring users have all the information to set up their secondary accounts correctly.

```markdown
<div align="center">

[![Galaxy Brain Banner](https://raw.githubusercontent.com/Shineii86/GalaxyBrain/main/images/GalaxyBrain.png)](https://github.com/Shineii86/GalaxyBrain)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Shineii86/GalaxyBrain/blob/main/notebooks/GalaxyBrain.ipynb)
[![Python 3.8+](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[![GitHub Stars](https://img.shields.io/github/stars/Shineii86/GalaxyBrain?style=for-the-badge)](https://github.com/Shineii86/GalaxyBrain/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/Shineii86/GalaxyBrain?style=for-the-badge)](https://github.com/Shineii86/GalaxyBrain/fork)

A **fully automated** Python script that runs in **Google Colab** to earn the **Galaxy Brain** achievement by creating accepted answers in GitHub Discussions.

</div>

---

> [!WARNING]
> **This script automates interactions with GitHub Discussions to artificially trigger the Galaxy Brain achievement.**
> - **Use responsibly.** Inflating achievements may be viewed negatively by potential employers or collaborators, and may violate GitHub's Terms of Service.
> - You need **Personal Access Tokens (classic)** with `repo` and `write:discussion` scopes for **each account** involved (main + at least two secondaries).
> - The script creates discussions and answers in your repository. **Ensure Discussions are enabled** in repository settings.
> - This tool is intended for **educational purposes and personal experimentation** only.

---

## 📖 Table of Contents

- [What is This Tool?](#-what-is-this-tool)
- [Why Use This Method?](#-why-use-this-method)
- [Prerequisites](#-prerequisites)
  - [1. Required Accounts](#1-required-accounts)
  - [2. Enable Discussions on Your Repository](#2-enable-discussions-on-your-repository)
  - [3. Generate Personal Access Tokens (Classic)](#3-generate-personal-access-tokens-classic)
  - [4. Add Secondary Accounts as Collaborators](#4-add-secondary-accounts-as-collaborators)
- [Step-by-Step Guide](#-step-by-step-guide)
- [Configuration Options](#-configuration-options)
- [How It Works](#-how-it-works-technical-overview)
- [Troubleshooting](#-troubleshooting)
- [License & Disclaimer](#-license--disclaimer)

---

## 🎯 What is This Tool?

This tool automates the process of earning the **Galaxy Brain** achievement on GitHub. Galaxy Brain is awarded when a user has **at least two answers marked as accepted** in GitHub Discussions.

Using the **GitHub GraphQL API**, the script:
1. Creates a discussion from your **main account**.
2. Posts an answer to that discussion from a **secondary account**.
3. Marks that answer as **accepted** using the main account.

This process is repeated until the desired number of accepted answers is reached (minimum **2** for the achievement).

> [!NOTE] This tool does **not** guarantee immediate achievement unlock. GitHub may take up to 24 hours to update achievement status.

---

## ✅ Why Use This Method?

| Feature                      | Benefit                                                                 |
|------------------------------|-------------------------------------------------------------------------|
| ☁️ **No PC Required**         | Runs entirely in Google Colab (cloud‑based). Works on any device with a browser. |
| 🔁 **Multi‑Account Support**  | Handles up to two secondary accounts (easily extendable).                |
| 📈 **Configurable Answers**   | Set the exact number of accepted answers you need.                       |
| 🛡️ **GraphQL API**            | Uses official GitHub APIs—no browser automation or scraping.             |
| 📦 **Minimal Dependencies**   | Only requires `requests` and standard libraries.                         |

---

## 🧰 Prerequisites

### 1. Required Accounts

- **One main GitHub account** – This account will receive the Galaxy Brain achievement.
- **At least two secondary GitHub accounts** – These accounts will post the answers that the main account accepts. You can use existing accounts or create new ones.

### 2. Enable Discussions on Your Repository

1. Go to the repository under your main account.
2. Click **Settings** → **Features**.
3. Under **Discussions**, check **Enable Discussions**.
4. A default category (e.g., "General") will be created—the script uses the first available category automatically.

### 3. Generate Personal Access Tokens (Classic)

You need a **Personal Access Token (Classic)** for **each account** (main and both secondaries). These tokens grant the script permission to act on behalf of each account.

> [!IMPORTANT]
> **Required scopes for all tokens (main and secondary):**
> - `repo` – Grants full control of private repositories (required for posting answers).
> - `write:discussion` – Grants read/write access to GitHub Discussions.

#### How to Create a Token

For **each account** (main, secondary1, secondary2), repeat these steps:

1. Log in to the account and go to **Settings** → **Developer settings** → **Personal access tokens** → **Tokens (classic)**.
2. Click **Generate new token** → **Generate new token (classic)**.
3. Give it a descriptive **Note** (e.g., `Galaxy Brain Script`).
4. Set an **Expiration** (e.g., 7 days – recommended for security).
5. Under **Select scopes**, check the following boxes:
   - ☑️ **repo** (this automatically selects all sub‑scopes under `repo`)
   - ☑️ **write:discussion** (under `write:discussion`)
6. Click **Generate token**.
7. **Copy the token immediately** (it starts with `ghp_`) and store it securely. You will not be able to see it again.

> 🔒 **Security Note:** Treat these tokens like passwords. Never commit them to a public repository or share them with anyone.

### 4. Add Secondary Accounts as Collaborators

The secondary accounts must have **write access** to your repository to post answers. You need to invite them as collaborators.

1. Go to your repository (under the main account) → **Settings** → **Collaborators and teams**.
2. Click **Add people** and enter the username of the first secondary account.
3. Click **Add to repository**.
4. Repeat for the second secondary account.

**Accept the Invitation:**
- Log in to each secondary account, go to `https://github.com/YOUR_MAIN_USERNAME/REPO_NAME` or check the email notification, and **accept the invitation**.

> ✅ **Verification:** You can confirm a secondary account has access by logging into that account and checking if you can see the repository in your list of repositories.

---

## 📥 How to Deploy

### 1️⃣ One‑Click Colab

<a href="https://colab.research.google.com/github/Shineii86/GalaxyBrain/blob/main/notebooks/GalaxyBrain.ipynb">
  <img src="https://user-images.githubusercontent.com/125879861/255389999-a0d261cf-893a-46a7-9a3d-2bb52811b997.png" alt="Open In Colab" width="200px">
</a>

### 2️⃣ Fill in the Configuration Form

Inside the Colab notebook, you'll find a single configuration cell with form fields:

| Variable                 | Description                                                               | Example Value               |
|--------------------------|---------------------------------------------------------------------------|-----------------------------|
| `MAIN_USERNAME`          | Your main GitHub handle (to earn the achievement)                         | `"Shineii86"`               |
| `MAIN_TOKEN`             | Personal Access Token for main account                                    | `"ghp_abc123..."`           |
| `SECONDARY_1_USERNAME`   | First secondary account handle                                            | `"helper1"`                 |
| `SECONDARY_1_TOKEN`      | Personal Access Token for first secondary account                         | `"ghp_def456..."`           |
| `SECONDARY_2_USERNAME`   | Second secondary account handle                                           | `"helper2"`                 |
| `SECONDARY_2_TOKEN`      | Personal Access Token for second secondary account                        | `"ghp_ghi789..."`           |
| `REPO_NAME`              | Target repository (must exist under `MAIN_USERNAME`)                      | `"galaxy-brain-demo"`       |
| `NUM_ANSWERS`            | Number of accepted answers to create (minimum 2 for Galaxy Brain)         | `2`                         |
| `ACTION_DELAY`           | Seconds to wait between API calls (increase to appear more natural)       | `5`                         |

### 3️⃣ Run the Notebook

Click **Runtime → Run all** (or press `Ctrl+F9`). The notebook will:
- Install `requests`
- Fetch your repository ID and discussion category
- For each requested answer:
  - Create a discussion (main account)
  - Post an answer (secondary account)
  - Mark the answer as accepted (main account)
- Display progress and final status

You'll see real‑time output like:

```
🧠 Galaxy Brain Automation for user 'Shineii86'
Repository: Shineii86/galaxy-brain-demo
Creating 2 accepted answer(s)

🔍 Fetching repository information...
✅ Found repository ID and category: General

--- Processing answer 1 of 2 ---
👤 Secondary account: helper1
📝 Creating discussion...
   📝 Discussion created: https://github.com/Shineii86/galaxy-brain-demo/discussions/1
💬 Posting answer as helper1...
   💬 Answer posted by secondary account
✅ Marking answer as accepted...
   ✅ Answer marked as accepted
🎉 Answer 1 accepted!

--- Processing answer 2 of 2 ---
...

==================================================
✨ Success! Created 2 accepted answer(s).
📊 Check your profile: https://github.com/Shineii86
🔔 Note: Achievements may take up to 24 hours to appear.
```

### 4️⃣ Check Your Achievements

1. Go to your GitHub profile: `https://github.com/YOUR_USERNAME`
2. Scroll down to the **Achievements** section (if you already have some) or visit `https://github.com/settings/achievements`.
3. **Galaxy Brain** should appear within 24 hours.

---

## ⚙️ Configuration Options

| Parameter                | Default | Description                                                                                                   |
|--------------------------|---------|---------------------------------------------------------------------------------------------------------------|
| `MAIN_USERNAME`          | —       | The GitHub username that will earn the achievement.                                                            |
| `MAIN_TOKEN`             | —       | PAT for the main account with `repo` and `write:discussion` scopes.                                            |
| `SECONDARY_1_USERNAME`   | —       | Username for the first secondary (answerer) account.                                                           |
| `SECONDARY_1_TOKEN`      | —       | PAT for the first secondary account with identical scopes.                                                     |
| `SECONDARY_2_USERNAME`   | —       | Username for the second secondary account.                                                                     |
| `SECONDARY_2_TOKEN`      | —       | PAT for the second secondary account.                                                                          |
| `REPO_NAME`              | —       | Repository name (under `MAIN_USERNAME`) where discussions will be created.                                     |
| `NUM_ANSWERS`            | `2`     | Number of accepted answers to create. Set to `2` for Galaxy Brain, or higher for testing.                      |
| `ACTION_DELAY`           | `5`     | Delay in seconds between API calls. Increase to `10–15` to mimic human behavior and reduce detection risk.     |

### Adding More Secondary Accounts

If you need more than two answers from distinct accounts, you can extend the `secondary_accounts` list inside the script:

```python
secondary_accounts = [
    {"username": SECONDARY_1_USERNAME, "token": SECONDARY_1_TOKEN},
    {"username": SECONDARY_2_USERNAME, "token": SECONDARY_2_TOKEN},
    {"username": "helper3", "token": "ghp_..."},  # Add more
]
```

---

## 🔬 How It Works (Technical Overview)

The script interacts with the **GitHub GraphQL API v4** using the following mutations:

1. **`createDiscussion`** – Creates a new discussion in the specified repository category.
2. **`addDiscussionComment`** – Posts a comment (answer) to a discussion.
3. **`markDiscussionCommentAsAnswer`** – Marks a comment as the accepted answer.

**Workflow:**

```
┌─────────────────┐     ┌─────────────────────┐     ┌──────────────────────┐
│  Main Account   │────▶│  Create Discussion  │────▶│  Discussion Created  │
└─────────────────┘     └─────────────────────┘     └──────────────────────┘
                                                               │
                                                               ▼
┌─────────────────────┐     ┌─────────────────┐     ┌──────────────────────┐
│ Secondary Account   │────▶│  Post Answer    │◀────│  Discussion ID       │
└─────────────────────┘     └─────────────────┘     └──────────────────────┘
                                      │
                                      ▼
                            ┌──────────────────────┐
                            │     Answer Comment ID    │
                            └──────────────────────┘
                                      │
                                      ▼
┌─────────────────┐     ┌─────────────────────────┐
│  Main Account      │───▶│  Mark as Accepted           │
└─────────────────┘     └─────────────────────────┘
```

All requests are authenticated via `Authorization: Bearer <TOKEN>` headers. Delays between actions help avoid rate limiting and make the activity appear more organic.

---

## 🆘 Troubleshooting

| Issue                                                      | Solution                                                                                     |
|------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| `Repository not found or no access`                        | Verify the repository name and that your main token has `repo` scope. Ensure the repository exists. |
| `Repository has no discussion categories`                  | Enable Discussions in repository settings (Settings → Features → Discussions).                |
| `GraphQL errors: ...` or `Bad credentials`                 | Your token is incorrect, expired, or lacks the required scopes (`repo`, `write:discussion`). |
| Secondary account cannot post answer                        | Ensure the secondary account has accepted the collaborator invitation to the repository.      |
| Achievement not appearing after 24 hours                    | Wait longer (up to 48 hours). Ensure you have **at least two** accepted answers. Check that the answers are still marked as accepted (not unmarked). |
| `Rate limit exceeded`                                      | Increase `ACTION_DELAY` or wait before running again. GitHub's GraphQL rate limit is generous (5,000 points/hour). |

---

## 📄 License & Disclaimer

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

> [!WARNING]
> This script is intended for **educational purposes and personal experimentation** only. Artificially triggering achievements may be viewed negatively by potential employers or collaborators, and may violate GitHub's Terms of Service. The author is not responsible for any consequences arising from misuse of this tool, including but not limited to account suspension, damage to professional reputation, or violation of platform terms.

---

### 🔗 Quick Links

- [Google Colab](https://colab.research.google.com/)
- [GitHub Personal Access Tokens](https://github.com/settings/tokens)
- [GitHub GraphQL API Documentation](https://docs.github.com/en/graphql)
- [GitHub Achievements](https://github.com/settings/achievements)

---

## 💕 Loved My Work?

🚨 [Follow me on GitHub](https://github.com/Shineii86)

⭐ [Give a star to this project](https://github.com/Shineii86/GalaxyBrain)

<div align="center">

<a href="https://github.com/Shineii86/GalaxyBrain">
<img src="https://github.com/Shineii86/AniPay/blob/main/Source/Banner6.png" alt="Banner">
</a>
  
  *For inquiries or collaborations*
     
[![Telegram Badge](https://img.shields.io/badge/-Telegram-2CA5E0?style=flat&logo=Telegram&logoColor=white)](https://telegram.me/Shineii86 "Contact on Telegram")
[![Instagram Badge](https://img.shields.io/badge/-Instagram-C13584?style=flat&logo=Instagram&logoColor=white)](https://instagram.com/ikx7.a "Follow on Instagram")
[![Pinterest Badge](https://img.shields.io/badge/-Pinterest-E60023?style=flat&logo=Pinterest&logoColor=white)](https://pinterest.com/ikx7a "Follow on Pinterest")
[![Gmail Badge](https://img.shields.io/badge/-Gmail-D14836?style=flat&logo=Gmail&logoColor=white)](mailto:ikx7a@hotmail.com "Send an Email")

  <sup><b>Copyright © 2026 <a href="https://telegram.me/Shineii86">Shinei Nouzen</a> All Rights Reserved</b></sup>

![Last Commit](https://img.shields.io/github/last-commit/Shineii86/GalaxyBrain?style=for-the-badge)

</div>
