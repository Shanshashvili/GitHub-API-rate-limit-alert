# 📬 GitHub Rate Limit Alert — Native Email Workflow (SMTP)

This workflow sends an email alert when your GitHub App approaches the API rate limit using a native SMTP client inside GitHub Actions.

---

## 🎯 Purpose

Automatically notify your team when GitHub API usage is running low, so you can respond before hitting hard limits and causing CI/CD or integration failures.

---

## 📄 Workflow File: [gh-native-alert.yml](.github/workflows/gh-native-alert.yml)

---

## 🛠️ Required Secrets

| Secret Name       | Description                      |
| ----------------- | -------------------------------- |
| `APP_ID`          | GitHub App ID (from setup guide) |
| `RSA_PRIVATE_KEY` | PEM contents of GitHub App key   |
| `SMTP_USERNAME`   | Your email address               |
| `SMTP_PASSWORD`   | Your email password/app password |

---

## 🔍 How to Test

1. Trigger manually via GitHub UI (`workflow_dispatch` enabled)
2. Lower the condition temporarily:

   ```yaml
   if: steps.rate_limit.outputs.rate_remaining < 5000
   ```
3. Check the logs and validate email delivery

---

## ⚠️ SMTP Tips

* Office365 (`smtp.office365.com`, port `587`) supports modern authentication
* If using Gmail, use `smtp.gmail.com` and create an **App Password**
* Avoid using personal credentials — use a team/automation mailbox
* Some companies (like EPAM) may block SMTP auth — use Microsoft Graph method if needed

---

Once tested and running, you’ll get alerted any time rate limits get dangerously low 🚨
