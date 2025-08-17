# 📬 GitHub Rate Limit Alert — Azure Graph API Workflow

This workflow uses **Microsoft Graph API** to send an alert email when your GitHub App approaches the API rate limit. It avoids SMTP issues and leverages secure Azure app permissions.

---

## 🎯 Purpose

Send alerts securely using Microsoft 365 via OAuth2 token, without relying on legacy SMTP or app passwords.

---

## 📄 Workflow File: [gh-azure-graph-alert.yml](.github/workflows/gh-azure-graph-alert.yml)

---

## 🔐 Required Secrets

| Secret Name       | Description                                 |
| ----------------- | ------------------------------------------- |
| `APP_ID`          | GitHub App ID                               |
| `RSA_PRIVATE_KEY` | PEM contents of GitHub App key              |
| `CLIENT_ID`       | Azure App's Application (client) ID         |
| `CLIENT_SECRET`   | Azure App's client secret                   |
| `TENANT_ID`       | Azure Active Directory tenant ID            |
| `MAIL_FROM`       | Mailbox to send from (must exist in tenant) |
| `MAIL_TO`         | Recipients (comma-separated if multiple)    |

---

## ✅ Azure Setup Summary

Make sure you've:

1. Registered an app in Azure
2. Granted **Mail.Send** permission (Application type)
3. Generated client secret
4. Granted **admin consent**
5. Added all values as GitHub secrets

See: [./github-app-setup.md](github-app-setup.md)

---

## 🧪 Testing

* Run manually with `workflow_dispatch`
* Temporarily raise the limit to test:

  ```yaml
  if: steps.rate_limit.outputs.rate_remaining < 5000
  ```

---

## ✅ Why Use Graph API?

* Works with 2FA and modern authentication
* Avoids SMTP firewalls and blocked ports
* Better compliance for Microsoft 365 tenants

Once deployed, this will silently protect your org with secure alerts 💌
