# Track iOS app sizes with trend alerts using Google Sheets and Gmail notifications

This workflow automatically records iOS app binary sizes (from App Store Connect or manual inputs) into Google Sheets, tracks size changes over time, generates trend alerts when sizes exceed thresholds, and sends Gmail notifications with summary details and links — helping teams monitor app growth and maintain size discipline. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))

---

## ⚡ Quick Start – Implementation Steps

1. Import this workflow JSON into your n8n instance. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))
2. Connect **Google Sheets OAuth2** credentials.
3. Connect **Gmail OAuth2** credentials for sending notifications.
4. In your Google Sheet, create or specify columns such as:
   - `Date`
   - `Version`
   - `Binary Size (MB)`
   - `Platform`
   - `Notes`
5. Set your **size threshold** for trend alerts in the configuration node.
6. Run the workflow manually or schedule it to run weekly/daily. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))

---

## 📌 What It Does

This workflow:

- Accepts iOS app size data either from App Store Connect webhooks or manual POST JSON payloads.
- Appends new size records into a **Google Sheet** for historical tracking.
- Compares new sizes against previous entries to detect abnormal growth.
- If a size exceeds your configured threshold, it triggers a **Gmail alert**.
- Includes metadata such as version and notes in both the sheet and alert email.
- Can be scheduled to run at set intervals (e.g., weekly).
- Helps detect regressions or major size bloat early. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))

---

## 👥 Who’s It For

This workflow is ideal for:

- iOS engineering teams monitoring app size trends over versions.
- DevOps & QA teams ensuring binary size standards are met.
- Release managers tracking binary bloat before shipping updates.
- Product owners interested in size benchmarks per platform.
- Anyone using Google Sheets and Gmail for lightweight dashboards and alerts. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))

---

## 🛠 Requirements

To use this workflow, you need:

- An **n8n instance** (cloud or self‑hosted).
- **Google Sheets OAuth2 credentials** with access to read/write your tracking sheet.
- **Gmail OAuth2 credentials** to send notification emails.
- A **Google Sheet** with at least columns for date, version, and size.
- Optionally, a mechanism (CI/CD or webhook) to POST iOS size data automatically. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))

---

## ⚙️ How It Works & Setup

### 1. Trigger

- The workflow can be triggered manually, scheduled (daily/weekly), or via webhook (from CI/CD pipeline sending current binary size).

### 2. Parse Input

- The incoming data payload should include fields such as `version`, `sizeMB`, `platform`, and optional `notes`.

### 3. Append to Google Sheets

- A **Google Sheets** node appends the new record into your historical size tracking sheet.

### 4. Size Comparison

- A **function** node compares the latest size against previous entries to check if it exceeds your configured threshold (e.g., percentage increase or fixed MB limit).

### 5. Conditional Alert

- If the threshold is breached, a **Gmail node** sends a formatted email alert including:
  - Version
  - Current size
  - Previous size
  - Change %
  - Notes & links (if provided)

### 6. Logging

- If no threshold breach occurs, the workflow simply logs the data and ends without sending an alert.

---

## 🛠 How to Customize Nodes

### Change Threshold Logic

- Update the logic in the **function node** that calculates size change percentage or fixed size limit.
- You can use MB, percentage, or multi‑tier thresholds for warnings vs critical alerts.

### Google Sheets Structure

- Add extra columns like `Build Number`, `Build URL`, `Commit SHA`, `Branch`, etc.
- Modify the append node to write these additional fields.

### Gmail Notifications

- Customize the subject, body, and recipients in the Gmail node.
- Include more contextual info (build link, release notes, CI status).

### Scheduling

- Modify the **Schedule Trigger** to run based on your release cadence (daily, weekly, after builds).
- Combine with webhooks to auto‑fire after each CI build.

---

## ➕ Add‑Ons (Optional Enhancements)

You can extend this workflow with:

- **Slack or Teams alerts** alongside Gmail.
- Attach PDF reports generated from Sheets summarizing size trends.
- Integrate with JIRA to file size‑bloat issues automatically.
- Dashboards (Google Data Studio/Tableau) consuming the same sheet.
- Track multiple platforms (iOS, Android) within the same sheet.
- Store build artifacts and size metrics in cloud storage (S3, GCS). ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))

---

## 📈 Use Case Examples

1. **Daily CI Integration** — Post build sizes automatically and receive alerts for major increases.
2. **Release Week Monitoring** — Track size regressions before shipping to app stores.
3. **Cross‑Team Transparency** — Share Google Sheets dashboards with leadership.
4. **Multiple Flavor Tracking** — Monitor sizes for dev/test/staging builds separately.
5. **Android + iOS Comparison** — Use one sheet to compare cross‑platform trends. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))

---

## 🧪 Troubleshooting Guide

| **Issue**               | **Possible Cause**                | **Solution**                                  |
| ----------------------- | --------------------------------- | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| No entries added        | Wrong Sheet ID or name            | Check the Google Sheet ID and sheet tab name  |
| Alert not sent          | Threshold logic never triggered   | Adjust threshold percentage or MB limit       |
| Email fails             | Gmail OAuth expired               | Reconnect Gmail credentials in n8n            |
| Wrong data format       | Payload missing fields            | Ensure payload includes version & size fields |
| Workflow not triggering | Schedule or webhook misconfigured | Review schedule or webhook settings           | ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com)) |

---

## 💬 Need Help?

Need help configuring the sheet schema, integrating your CI pipeline, or adding advanced alert logic (Slack, critical vs warning tiers, dashboards)? Our n8n automation experts at **WeblineIndia** can assist with tailored work — from onboarding to full workflow optimization. ([n8n.io](https://n8n.io/workflows/9617-track-ios-app-sizes-with-trend-alerts-using-google-sheets-and-gmail-notifications/?utm_source=chatgpt.com))
