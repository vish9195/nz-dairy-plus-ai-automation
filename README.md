# NZ Dairy Plus — AI Automation System

AI-powered upsell and subscription system built for a NZ dairy distributor.

## What it does
- **System 1:** Market basket analysis to identify upsell opportunities
- **System 2:** Pattern recognition to detect recurring order candidates  
- **System 3:** Claude API generates personalized SMS/email outreach

## Tech stack
Python · Pandas · NumPy · Anthropic Claude API · JSON automation queue

## How to run
1. Install dependencies: `pip install anthropic pandas numpy`
2. Set API key: `export ANTHROPIC_API_KEY=your-key`
3. Open `dairy_automation.ipynb` and run all cells

## Outputs
- `data/sample_orders.csv` — order data
- `outputs/upsell_rules.csv` — association rules
- `outputs/patterns.csv` — recurring order patterns  
- `outputs/automation_queue.json` — messages ready to send to Twilio/SendGrid

## Author
V P Vishal | Master of Business Analytics, University of Auckland
