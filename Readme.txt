# 🧀 NZ Dairy Plus - AI Data & Automation System

**Smart Upsell Assistant + Missed Opportunity Finder**

[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **AI-powered customer intelligence system that analyzes purchase patterns to drive automated upsells and recurring order conversions.**

Built by **V P Vishal** | Master of Business Analytics, University of Auckland

---

## 🎯 Project Overview

This system solves two critical business problems for NZ Dairy Plus:

### **System 1: Smart Upsell Assistant**
Identifies logical product add-ons using Market Basket Analysis. When a customer orders milk, the system automatically suggests cheese, cream, or other complementary products before order deadlines.

**Key Features:**
- Association rule learning to find product relationships
- Confidence scoring (how likely is the upsell to convert?)
- Automated SMS/email trigger generation
- Lift calculation (are products truly related, or just coincidence?)

### **System 2: Missed Opportunity Finder**
Detects predictable ordering patterns and flags customers for recurring order subscriptions.

**Key Features:**
- Pattern recognition across purchase history
- Consistency scoring (how reliable is this pattern?)
- Day-of-week preference detection
- Automated subscription prompt generation

---

## 🚀 Quick Start

### Prerequisites
```bash
Python 3.8 or higher
pip (Python package manager)
```

### Installation

1. **Clone this repository:**
```bash
git clone https://github.com/YOUR_USERNAME/nz-dairy-plus-demo.git
cd nz-dairy-plus-demo
```

2. **Install dependencies:**
```bash
pip install -r requirements.txt
```

3. **Run the demo:**
```bash
python main.py
```

That's it! The system will:
- Generate sample order data
- Analyze patterns
- Display upsell recommendations
- Show subscription opportunities
- Output automation-ready triggers

---

## 📊 Sample Output

### Smart Upsell Rules Discovered:
```
if_bought    recommend    confidence    support    lift
milk         cheese       0.78          0.45       2.1
cream        butter       0.65          0.32       1.8
milk         cream        0.58          0.38       1.6
```

### Predictable Purchase Patterns:
```
customer     product    avg_gap_days    consistency    preferred_day
CUST_023     cream      7.2             0.89           Friday
CUST_041     milk       14.1            0.82           Monday
CUST_017     cheese     10.5            0.76           Thursday
```

### Automated Message Example:
```
Hi CUST_001! 🧀 Based on your order (milk), customers also love 
adding: cheese. Add it before your order deadline? Reply YES 
to add it now.
```

---

## 🛠️ Technical Architecture

### System 1: Market Basket Analysis
```python
# Core algorithm: Association Rule Learning
1. Calculate support: P(A ∩ B) - How often do items appear together?
2. Calculate confidence: P(B|A) - If A bought, probability of B?
3. Calculate lift: Confidence / P(B) - Is this better than random?
```

**Why this approach?**
- Support filters out rare combinations (noise)
- Confidence measures recommendation strength
- Lift ensures genuine relationships (not just popular products)

### System 2: Pattern Recognition
```python
# Core algorithm: Time-series pattern detection
1. Group orders by customer + product
2. Calculate average gap between orders
3. Measure consistency (low std deviation = predictable)
4. Flag when customer is "due" for next order
5. Identify preferred day of week
```

**Why this approach?**
- Focuses on behavioral consistency, not just frequency
- Accounts for irregular customers (filters them out)
- Predicts next order date for proactive outreach

---

## 📁 Project Structure

```
nz-dairy-plus-demo/
├── main.py                    # Main execution script with demo
├── requirements.txt           # Python dependencies
├── README.md                  # This file
├── src/
│   ├── __init__.py
│   ├── upsell_assistant.py   # System 1: Market basket analysis
│   ├── opportunity_finder.py # System 2: Pattern detection
│   ├── automation_triggers.py # SMS/Email generation
│   └── data_generator.py     # Sample data creation
├── data/
│   └── sample_orders.csv     # Generated sample dataset
├── outputs/
│   ├── upsell_rules.csv      # Discovered associations
│   ├── patterns.csv          # Detected recurring patterns
│   └── automation_queue.json # Messages ready to send
└── docs/
    ├── technical_approach.md  # Detailed methodology
    └── business_impact.md     # ROI analysis
```

---

## 🔌 Integration Points

### Current Implementation:
- ✅ CSV data ingestion
- ✅ Python-based analysis
- ✅ JSON output for automation tools

### Production-Ready Integrations:

**Data Input:**
```python
# Option 1: CSV Upload
df = pd.read_csv('customer_orders.csv')

# Option 2: API Connection
df = fetch_from_api('https://api.nzdairyplus.com/orders')

# Option 3: Database Query
df = pd.read_sql('SELECT * FROM orders', conn)
```

**Automation Output:**
```python
# Twilio (SMS)
client.messages.create(
    to=customer_phone,
    from_='+64XXXXXXX',
    body=upsell_message
)

# SendGrid (Email)
message = Mail(
    from_email='orders@nzdairyplus.com',
    to_emails=customer_email,
    subject='We thought you might like...',
    html_content=upsell_email
)

# Zapier Webhook
requests.post('https://hooks.zapier.com/hooks/catch/xxxxx/', 
              json=automation_trigger)
```

---

## 📈 Business Impact

### Expected Results:

| Metric | Current (Manual) | With Automation | Improvement |
|--------|------------------|-----------------|-------------|
| Average Order Value | $45 | $52-56 | +15-25% |
| Recurring Orders | 15% of customers | 45-55% | +3x |
| Outreach Time | 10 hrs/week | 2 hrs/week | -80% |
| Conversion Rate | 12% (manual) | 25-30% (automated) | +2x |

### ROI Calculation:
```
If 500 active customers:
- Upsells: 500 × 20% conversion × $8 avg add-on = $800/week additional revenue
- Subscriptions: 500 × 30% × $45 monthly = $6,750/month recurring revenue
- Time saved: 8 hrs/week × $30/hr = $240/week operational savings

Total annual impact: ~$100,000+ in revenue + $12,000 cost savings
Development investment: 40-60 hours
```

---

## 🧪 Testing & Validation

### Current Test Coverage:
- ✅ Market basket analysis with 500 sample orders
- ✅ Pattern detection across 90-day history
- ✅ Edge cases (new customers, irregular orders)
- ✅ Automation trigger formatting

### Next Steps for Production:
1. **A/B Testing:** Split customers into control vs automated groups
2. **Conversion Tracking:** Monitor which recommendations convert
3. **Pattern Accuracy:** Measure prediction accuracy over time
4. **Message Optimization:** Test different copy/timing variations

---

## 🛣️ Implementation Roadmap

### Phase 1: Proof of Concept (Week 1-2)
- ✅ Core algorithms implemented
- ✅ Sample data validation
- ✅ Basic automation triggers

### Phase 2: Real Data Integration (Week 3-4)
- Connect to actual customer database
- Validate accuracy on historical data
- Tune confidence/support thresholds

### Phase 3: Automation Setup (Week 5-6)
- Integrate Twilio for SMS
- Setup SendGrid email templates
- Create Zapier workflows

### Phase 4: Monitoring & Optimization (Week 7-8)
- Build conversion tracking dashboard
- A/B test message variations
- Refine recommendation logic based on results

---

## 🤝 About the Developer

**V P Vishal**  
Master of Business Analytics (with Merit) - University of Auckland  
Specialization: FinTech

**Relevant Experience:**
- Built customer analytics pipeline processing 20,000+ data points for Financial Services Council
- Developed predictive models achieving 85% accuracy in customer behavior forecasting
- Created automated ETL workflows reducing processing time by 25%
- Strong foundation in Python, Pandas, NumPy, machine learning, and business intelligence

**Technical Skills:**
- **Languages:** Python, R, SQL
- **Data Science:** Pandas, NumPy, scikit-learn, statistical modeling
- **Automation:** API integration, Twilio, SendGrid, Zapier
- **Analytics:** Customer segmentation, predictive modeling, A/B testing
- **BI Tools:** Power BI, Tableau, data visualization

-
---

## 📝 License

MIT License - feel free to use this code as reference for your own projects.

---

## 🙏 Acknowledgments

- Market Basket Analysis methodology inspired by the Apriori algorithm
- Pattern detection based on time-series forecasting principles
- Built as a demonstration for NZ Dairy Plus AI Data & Automation Specialist role

---

**⭐ If this demo demonstrates the capabilities you're looking for, let's discuss how we can implement this for real customer data and drive measurable business results.**