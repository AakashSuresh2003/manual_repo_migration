# GitHub Repository Migration Workflow

This project provides a **GitHub Actions workflow** that helps you **manually migrate a repository** from one GitHub organization to another using the **GitHub Enterprise Importer (GEI) CLI**.

---

## How It Works

1. Trigger the workflow manually via the **Actions** tab.
2. Enter the required inputs (PATs, source/target orgs, and source repo name).
3. The workflow:
   - Downloads the GEI CLI
   - Queues a migration
   - Locks the source repo
   - Waits for the migration to complete
4. Migration status and output are logged in the workflow run.

---

## 🛠️ What’s Used

- **GitHub Actions**
- **PowerShell** scripting
- **GEI CLI** (GitHub Enterprise Importer)
- **GitHub REST & GraphQL APIs**

---

## Required Inputs

| Input Name         | Description                          |
|--------------------|--------------------------------------|
| `GH_SOURCE_PAT`    | PAT with access to the **source org** |
| `GH_PAT`           | PAT with access to the **target org** |
| `GH_SOURCE_ORG`    | Name of the source organization      |
| `GH_TARGET_ORG`    | Name of the target organization      |
| `GH_SOURCE_REPO`   | Name of the repository to migrate    |

> You’ll be prompted to enter these when you manually run the workflow.

---

## How to Get Your Personal Access Tokens (PATs)

1. Go to: [https://github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Generate new token (classic)**
3. Set expiration and scopes:
   - For source org token (`GH_SOURCE_PAT`):
     - `repo`, `read:org`, `admin:repo_hook`
   - For target org token (`GH_PAT`):
     - `repo`, `admin:org`, `admin:repo_hook`, `workflow`
4. Copy and save the token securely.

---

## How to Use PATs in This Workflow

You don’t need to store these in repository secrets.

Instead:
- Go to **Actions → Manual-Repository-Migration-Workflow**
- Click **Run workflow**
- Fill in all the required fields including the PATs

> Your tokens will be masked in logs but should still be handled carefully.

---

## Notes

- This is a **manual** workflow—ideal for migrating one repo at a time.
- Requires GitHub Enterprise Importer access and eligibility.

---
