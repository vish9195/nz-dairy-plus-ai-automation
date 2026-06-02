# NZ Dairy Plus — AI Automation System

> Automated upsell and subscription optimisation for a New Zealand dairy distributor, powered by market basket analysis and the Claude API.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Anthropic](https://img.shields.io/badge/Claude%20API-6B46C1?style=flat)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)

---

## What It Does

The system works in three stages:

| Stage | What happens |
|---|---|
| **Market Basket Analysis** | Finds product pairs that are frequently bought together (association rules via Apriori) |
| **Pattern Recognition** | Identifies customers with recurring order cycles who are candidates for subscriptions |
| **AI Outreach Generation** | Feeds each customer's purchase history into the Claude API to generate personalised SMS and email messages |

The output is a ready-to-send queue (`automation_queue.json`) that can be piped directly into an SMS/email delivery platform.

---

## Results

| Metric | Value |
|---|---|
| Association rules generated | Stored in `outputs/upsell_rules.csv` |
| Recurring order patterns detected | Stored in `outputs/patterns.csv` |
| Messages auto-generated | One per eligible customer, via Claude API |

---

## Project Structure

```
nz-dairy-plus-ai-automation/
├── dairy_automation.ipynb   # Main notebook — run top to bottom
├── data/
│   └── sample_orders.csv    # Sample input (see format below)
├── outputs/
│   ├── upsell_rules.csv     # Association rules
│   ├── patterns.csv         # Recurring order patterns
│   └── automation_queue.json # Generated messages ready for delivery
├── README.md
└── licence.txt
```

---

## Input Data Format

`data/sample_orders.csv` — one row per order line:

```
customer_id, order_date, product_name, quantity, unit_price
C001, 2024-01-03, Full Cream Milk 2L, 4, 3.50
C001, 2024-01-10, Full Cream Milk 2L, 4, 3.50
C002, 2024-01-05, Greek Yoghurt 500g, 2, 4.20
```

A minimal sample file is included so the notebook runs without real customer data.

---

## Setup & Usage

```bash
# 1. Clone the repo
git clone https://github.com/vish9195/nz-dairy-plus-ai-automation.git
cd nz-dairy-plus-ai-automation

# 2. Install dependencies
pip install pandas numpy anthropic mlxtend

# 3. Set your Claude API key
export ANTHROPIC_API_KEY="your-key-here"   # macOS/Linux
$env:ANTHROPIC_API_KEY="your-key-here"     # Windows PowerShell

# 4. Run the notebook
jupyter notebook dairy_automation.ipynb
```

Execute all cells in order. Outputs are written to the `outputs/` folder.

---

## Tech Stack

- **Python** — data processing and pipeline orchestration
- **Pandas / NumPy** — data wrangling
- **mlxtend** — Apriori algorithm and association rule mining
- **Anthropic Claude API** — personalised message generation
- **JSON** — structured output for delivery platforms

---

## Author

**V P Vishal** — Master of Business Analytics, University of Auckland  
[GitHub](https://github.com/vish9195) · [Email](mailto:vishalvp1963@gmail.com)
