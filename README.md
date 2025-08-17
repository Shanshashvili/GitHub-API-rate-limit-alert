# GitHub-API-rate-limit-alert# 🚨 GitHub API Rate Limit Alert System

This project helps monitor your GitHub App’s API usage and automatically sends an alert email when rate limits run low.

---

## 🔍 Why This Matters

If your automation (CI/CD, bots, integrations) relies on the GitHub API, hitting the rate limit can silently break pipelines or block key tasks. This repo prevents that.

---

## 🧰 Two Alerting Approaches

| Workflow                   | Description                                     |
| -------------------------- | ----------------------------------------------- |
| `gh-native-alert.yml`      | GitHub-native email alert using SMTP            |
| `gh-azure-graph-alert.yml` | Microsoft Graph API–based email alert via Azure |

Each method is fully documented in `/docs`.

---

## 📋 Prerequisites

* GitHub App installed at org level
* Secrets/variables configured (see docs)
* Azure app registration (for Graph API workflow only)

---

## 📚 Docs

* [GitHub App Setup](./github-app-setup.md)
* [GitHub Native Workflow](./native-workflow.md)
* [Azure Graph Workflow](./azure-graph-workflow.md)

---

## 🔗 Useful Links

* [GitHub REST API Rate Limits](https://docs.github.com/en/rest/rate-limit)
* [Create a GitHub App](https://docs.github.com/en/apps/creating-github-apps)
* [Microsoft Graph Mail.Send Permission](https://learn.microsoft.com/en-us/graph/permissions-reference#mail-permissions)
