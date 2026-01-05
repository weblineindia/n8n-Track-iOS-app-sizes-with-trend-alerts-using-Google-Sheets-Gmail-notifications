
# Track iOS App Sizes with Trend Alerts using Google Sheets and Gmail

This workflow automatically records **iOS app binary sizes** (from App Store Connect, CI/CD pipelines, or manual inputs) into **Google Sheets**, tracks size changes over time, and sends **Gmail alerts** when size thresholds are exceeded — helping teams monitor app growth and prevent size bloat early.

---

## ⚡ Quick Start – Implementation Steps

1. Import this workflow JSON into your **n8n** instance.
2. Connect **Google Sheets OAuth2** credentials.
3. Connect **Gmail OAuth2** credentials for notifications.
4. Create or configure a Google Sheet with the following columns:

   * `Date`
   * `Version`
   * `Binary Size (MB)`
   * `Platform`
   * `Notes`
5. Set your **size threshold** in the configuration or function node.
6. Run the workflow manually or schedule it (daily / weekly).

---

## 📌 What It Does

This workflow helps you maintain app size discipline by:

* Accepting iOS app size data via webhook, CI/CD, or manual input.
* Appending size records into **Google Sheets** for historical tracking.
* Comparing the latest size with previous versions.
* Detecting abnormal growth or regressions.
* Sending **Gmail alerts** when size thresholds are exceeded.
* Including version, platform, and notes in both Sheets and email alerts.
* Supporting scheduled or event-based execution.

---

## 👥 Who’s It For

This workflow is ideal for:

* **iOS engineering teams** tracking binary size growth
* **DevOps & QA teams** enforcing size limits
* **Release managers** validating builds before submission
* **Product owners** monitoring size trends
* Teams using **Google Sheets + Gmail** for lightweight reporting

---

## 🛠 Requirements

To run this workflow, you need:

* An **n8n instance** (cloud or self-hosted)
* **Google Sheets OAuth2 credentials** (read/write access)
* **Gmail OAuth2 credentials** for sending alerts
* A **Google Sheet** with version and size columns
* Optional: CI/CD pipeline or webhook to POST size data automatically

---

## ⚙️ How It Works

### 1. Trigger

* Workflow can run via:

  * Manual execution
  * Schedule trigger (daily / weekly)
  * Webhook from CI/CD pipeline

### 2. Parse Input

* Incoming payload should contain:

  * `version`
  * `sizeMB`
  * `platform`
  * Optional `notes`

### 3. Append to Google Sheets

* A **Google Sheets node** appends the new size entry.

### 4. Size Comparison

* A **function node** compares the latest size with previous entries.
* Supports fixed MB thresholds or percentage growth logic.

### 5. Conditional Alert

* If the threshold is breached, a **Gmail node** sends an alert with:

  * App version
  * Current size
  * Previous size
  * Size increase (% or MB)
  * Notes or build context

### 6. Logging Only

* If no threshold is exceeded, the workflow logs the data and exits.

---

## 🛠 How to Customize

### Threshold Logic

* Modify the function node to:

  * Use percentage growth
  * Use fixed MB limits
  * Add warning vs critical tiers

### Google Sheets Structure

* Add extra columns such as:

  * Build number
  * Commit SHA
  * Branch name
  * Build URL
* Update the append node accordingly.

### Gmail Notifications

* Customize subject, message body, and recipients.
* Add CI links, release notes, or dashboards.

### Scheduling

* Adjust the schedule trigger based on your release cadence.
* Combine schedule + webhook for hybrid execution.

---

## ➕ Optional Enhancements

You can extend this workflow to:

* Send alerts to **Slack or Microsoft Teams**
* Generate PDF or summary reports from Sheets
* Create **Jira tickets** for critical size regressions
* Build dashboards using Looker Studio or Tableau
* Track **Android + iOS** sizes in a single sheet
* Store artifacts and metrics in cloud storage (S3, GCS)

---

## 📈 Use Case Examples

1. CI pipelines post build sizes automatically after each build
2. Detect size regressions before App Store submission
3. Share size-trend dashboards with stakeholders
4. Track multiple build flavors (dev, staging, prod)
5. Compare iOS and Android binary size growth over time

---

## 🧪 Troubleshooting Guide

| Issue                   | Possible Cause                    | Solution                                  |
| ----------------------- | --------------------------------- | ----------------------------------------- |
| No entries added        | Wrong Sheet ID or tab name        | Verify Google Sheet ID and worksheet name |
| Alert not sent          | Threshold never triggered         | Lower percentage or MB threshold          |
| Email fails             | Gmail OAuth expired               | Reconnect Gmail credentials               |
| Wrong data logged       | Payload missing fields            | Ensure payload includes version & size    |
| Workflow not triggering | Schedule or webhook misconfigured | Review trigger configuration              |

---

## 💬 Need Help?

Need help integrating CI pipelines, designing size dashboards, or adding advanced alert logic (Slack, Jira, severity tiers)?

The **WeblineIndia n8n automation team** can help with:

* CI/CD & mobile workflow automation
* Google Sheets & reporting setups
* Advanced alerting logic
* End-to-end n8n workflow optimization

🚀 Reach out for expert n8n automation support.