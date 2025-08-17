# 🛠️ GitHub App Setup Guide

This guide walks you through creating and configuring a GitHub App to monitor API rate limits and authenticate securely within GitHub Actions.

---

## 🔧 Step 1: Create the GitHub App

1. Visit [https://github.com/settings/apps](https://github.com/settings/apps)
2. Click **"New GitHub App"**
3. Fill in the required fields:

| Field               | Value                         |
| ------------------- | ----------------------------- |
| **GitHub App name** | `gh-rate-monitor` (or custom) |
| **Homepage URL**    | `https://your-org.github.io`  |
| **Callback URL**    | *(leave blank)*               |
| **Webhook URL**     | *(optional)*                  |
| **Webhook secret**  | *(optional, but recommended)* |

4. Under **Repository permissions**, set:

   * `Actions` → `Read-only`
   * `Metadata` → `Read-only`

5. Uncheck all user permissions

6. Under **Where can this GitHub App be installed?** → select `Only on this account`

7. Click **Create GitHub App**

---

## 📑 Step 2: Locate Required Info for GitHub Actions

After your app is created, go to its **Overview** page. Note down:

* 🔹 **App ID**
* 🔹 **Slug** (used in URLs, like `gh-rate-monitor`)

You'll need these for workflows.

---

## 🔧 Step 3: Install the GitHub App to Your Org

1. On the GitHub App page, click **Install App**
2. Choose your organization
3. Select **All repositories** (or specific ones you want to monitor)

---

## 🔐 Step 4: Generate and Download the Private Key (.pem)

1. In your app settings → scroll to **Private keys**
2. Click **Generate a private key**
3. This will download a `.pem` file to your machine — keep it secure and do not rename it

---

## 📥 Step 5: Upload Secrets to GitHub Repository

Go to your GitHub repo → **Settings** → **Secrets and variables → Actions** → **New repository secret**

Add the following:

| Secret Name       | Value                           |
| ----------------- | ------------------------------- |
| `APP_ID`          | The App ID from GitHub App page |
| `RSA_PRIVATE_KEY` | Contents of the `.pem` file     |

### ✅ Use GitHub CLI for Uploading `.pem`

This is the safest way to ensure line breaks are preserved:

```bash
gh secret set RSA_PRIVATE_KEY < path/to/your-app.pem
```

➡️ Requires [GitHub CLI](https://cli.github.com/) and `gh auth login` to be configured.

---

## ✅ Done!

You’ve now:

* Created a GitHub App
* Noted down App ID and slug
* Installed the app at the organization level
* Generated the `.pem` key
* Uploaded required secrets securely

You’re now ready to plug the app into your workflows!
