# 🛡️ Manage Governance via Azure Policy

## 📘 Lab Overview
This lab demonstrates how to implement governance strategies in Azure using resource tagging, policy enforcement, remediation, and resource locks. These practices align with the Microsoft Well-Architected Framework and Cloud Adoption Framework.

> ⏱️ Estimated Duration: ~30 minutes  
> 🌍 Region Used: East US  
> 📦 Resource Group: `az104-rg2`

---

## 🔧 Task 1: Assign Tags via Azure Portal

**Goal:** Create a resource group and assign a governance tag.

### Steps:
- Navigate to **Resource groups** → **+ Create**
- Configure:
  - Resource Group Name: `az104-rg2`
  - Location: East US
- Add Tag:
  - Name: `Cost Center`
  - Value: `000`
- Click **Review + Create** → **Create**

---

## 🛡️ Task 2: Enforce Tagging via Azure Policy

**Goal:** Prevent resource creation without the required tag.

### Steps:
- Go to **Policy** → **Definitions**
- Search: `Require a tag and its value on resources`
- Assign Policy to:
  - Scope: `az104-rg2`
- Parameters:
  - Tag Name: `Cost Center`
  - Tag Value: `000`
- Attempt to create a Storage Account without the tag → **Validation fails**

---

## 🔁 Task 3: Apply Tagging via Azure Policy

**Goal:** Automatically apply missing tags to existing resources.

### Steps:
- Delete previous policy assignment
- Assign: `Inherit a tag from the resource group if missing`
- Scope: `az104-rg2`
- Parameters:
  - Tag Name: `Cost Center`
- Enable remediation task
- Create a Storage Account → **Tag is auto-applied**

---

## 🔒 Task 4: Configure and Test Resource Locks

**Goal:** Prevent accidental deletion of critical resources.

### Steps:
- Go to **Resource Group** → **Settings** → **Locks**
- Add Lock:
  - Name: `rg-lock`
  - Type: `Delete`
- Attempt to delete resource group → **Deletion blocked**

---

## ✅ Skills Demonstrated

- Azure governance via tagging and policy
- Policy enforcement and remediation
- Resource protection using locks
- Audit-ready cloud configuration

---

## 📸 Screenshot Suggestions

> Include only key screenshots to keep the doc clean:
- Tags tab during resource group creation
- Policy assignment summary
- Validation failed message
- Remediation tab with managed identity warning
- Tags blade showing auto-applied tag
- Lock settings and deletion failure message

---

## 🧠 Notes

- Policies may take 5–10 minutes to take effect.
- Always avoid exposing subscription IDs, keys, or credentials in screenshots.
- This lab is ideal for showcasing governance skills on GitHub and LinkedIn.
