# HC Forward — Governance Board Voting App

A live, browser-based voting tool for HC Forward governance board meetings. Board members can score business cases in real time from any device, with results written directly to Smartsheet.

---

## How It Works

- Each board member opens the app on their own device (phone, tablet, or laptop)
- Voters score a business case across **7 sections** and **20 questions**, each rated **1–3**
- Maximum total score: **60 points**
- The facilitator sees a live dashboard with aggregated scores, section breakdowns, and a verdict
- All votes are stored permanently in a Smartsheet sheet

---

## Scoring Scale

| Score | Label |
|-------|-------|
| 1 | Weak |
| 2 | Adequate |
| 3 | Strong |

## Verdict Thresholds

| Score Range | Verdict |
|-------------|---------|
| 45 – 60 | ✅ Strong Recommend |
| 35 – 44 | 🟡 Conditional Approve |
| 25 – 34 | 🟠 Needs Development |
| 0 – 24 | 🔴 Not Recommended |

---

## Evaluation Sections

| # | Section | Questions |
|---|---------|-----------|
| 1 | Market Opportunity | 3 |
| 2 | Value Proposition | 2 |
| 3 | Financial Viability | 4 |
| 4 | Strategic Alignment | 2 |
| 5 | Product Feasibility | 3 |
| 6 | Risk Assessment | 3 |
| 7 | Go-to-Market Plan | 3 |

---

## Setup & Infrastructure

### Hosting
The app is hosted on **GitHub Pages** and is accessible from any device on any network:
```
https://yourusername.github.io/hcforward-voting
```

### Smartsheet Integration
Votes are written to Smartsheet via a **Cloudflare Worker** proxy (`smartsheet-proxy.hnussman.workers.dev`). The Worker handles authentication and CORS, so no API token is ever exposed to voters.

### Shareable Link
To skip the setup screen, share a pre-filled link with the Sheet ID included:
```
https://yourusername.github.io/hcforward-voting?sheet=YOUR_SHEET_ID
```

---

## Running a Meeting

### Before the Meeting
1. Log into the app and click **Create Sheet & Continue** to generate a fresh Smartsheet sheet
2. Copy the Sheet ID shown on screen
3. Build the shareable link with the Sheet ID and send it to all board members
4. Do a quick test vote with a colleague to confirm everything is writing to Smartsheet correctly

### During the Meeting
- **Facilitator** opens the link → selects **"I'm the Facilitator"** → monitors the live dashboard
- **Voters** open the link → select **"I'm a Voter"** → enter their name → vote through all 7 sections → submit
- The facilitator dashboard auto-refreshes every **5 seconds**

### After the Meeting
- Click **⬇️ Export CSV** on the facilitator screen to download all votes
- Click **🗑️ Reset** to clear votes from Smartsheet before the next business case presentation

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| Frontend | Vanilla HTML, CSS, JavaScript |
| Hosting | GitHub Pages |
| API Proxy | Cloudflare Workers |
| Data Storage | Smartsheet |

---

## Making Changes

To update the app:
1. Edit `index.html` in this repository
2. Commit the changes
3. GitHub Pages will automatically redeploy within ~60 seconds
