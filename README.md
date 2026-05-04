
# Bank-Marketing-Analysis# Bank Marketing Campaign Performance Dashboard

##  Project Overview
A comprehensive Power BI and MySQL analytics solution analyzing 45,211 customer records from a Portuguese bank's direct marketing campaigns to optimize targeting strategies and improve conversion rates.

##  Objectives
- Evaluate marketing campaign effectiveness and ROI
- Identify high-converting customer segments
- Optimize contact frequency to reduce costs
- Provide actionable insights for targeted marketing strategies

##  Key Metrics
- **Total Customers Analyzed:** 45,211
- **Total Conversions:** 5,289 subscriptions
- **Overall Conversion Rate:** 11.70%
- **Average Contact Attempts:** 2.76
- **Campaign Efficiency:** 1.91K conversions per optimal contact

##  Tools & Technologies
- **MySQL:** Data extraction, filtering, and segmentation
- **Power BI:** Interactive dashboard and visualization
- **Python (Pandas):** Data preprocessing and EDA
- **DAX:** Advanced metrics and calculated measures

##  Key Features
- **Conversion Rate Analysis:** By job, education, age, and marital status
- **Campaign Performance:** Monthly trend tracking and efficiency metrics
- **Contact Optimization:** Analysis of diminishing returns on contact attempts
- **Customer Segmentation:** Targeting quadrant based on balance and conversion
- **Demographic Insights:** Age group and occupation-based performance
- **Temporal Patterns:** Monthly and seasonal campaign effectiveness

##  Key Insights

### Top Converting Segments:
1. **Students:** 15-18% conversion rate (50% above average)
2. **Retirees:** 15-18% conversion rate
3. **Management:** 12-14% conversion rate

### Optimal Contact Strategy:
- **2-3 contact attempts** maintain 12% conversion efficiency
- Beyond 3 attempts, conversion drops sharply
- **Recommendation:** Reduce costs by 30% through optimized contact frequency

### Demographic Patterns:
- Age groups 30-40 show highest engagement
- Balance range impacts conversion probability
- Previous campaign success strongly predicts future conversion

##  Dataset Information
- **Source:** Portuguese bank direct marketing campaigns
- **Records:** 45,211 customer contacts
- **Features:** 17 attributes including demographics, account info, campaign details
- **Target Variable:** Term deposit subscription (yes/no)

### Key Columns:
- Age, Job, Marital Status, Education
- Account Balance, Credit Default, Housing Loan
- Contact Type, Campaign Attempts, Previous Outcome
- Subscription Result (Target)

##  SQL Queries Included

### 1. Conversion Rate by Job Type 
SELECT job, 
       COUNT(*) as total_customers,
       SUM(CASE WHEN y = 'yes' THEN 1 ELSE 0 END) as conversions,
       ROUND(100.0 * SUM(CASE WHEN y = 'yes' THEN 1 ELSE 0 END) / COUNT(*), 2) as conversion_rate
FROM bank_marketing
GROUP BY job
ORDER BY conversion_rate DESC;


###  2. Monthly Campaign Performance

SELECT month,
       COUNT(*) as contacts,
       SUM(CASE WHEN y = 'yes' THEN 1 ELSE 0 END) as conversions,
       ROUND(100.0 * SUM(CASE WHEN y = 'yes' THEN 1 ELSE 0 END) / COUNT(*), 2) as conv_rate
FROM bank_marketing
GROUP BY month
ORDER BY conv_rate DESC;


### 3. Contact Frequency Effectiveness

SELECT campaign as contact_attempts,
       COUNT(*) as customers,
       ROUND(AVG(CASE WHEN y = 'yes' THEN 1 ELSE 0 END) * 100, 2) as conversion_rate
FROM bank_marketing
GROUP BY campaign
HAVING COUNT(*) > 100
ORDER BY campaign;


##  How to Use

### Dashboard:
1. Download the `.pbix` file from this repository
2. Open in Power BI Desktop
3. Use interactive filters (Education, Job, Contact Type, Month)
4. Explore different customer segments and patterns

### SQL Analysis:
1. Import `bank-full.csv` into MySQL
2. Run provided SQL queries for custom analysis
3. Modify queries for specific business questions

##  Dashboard Preview
[Add screenshot of your dashboard here]

##  Business Recommendations

### Immediate Actions:
1. Focus on high-converting segments: Students and retirees
2. Optimize contact frequency: Limit to 2-3 attempts
3. Timing matters: Target campaigns during peak conversion months
4. Balance targeting: Focus on mid-to-high balance customers

### Long-term Strategy:
1. Develop segment-specific messaging for students vs. retirees
2. Implement predictive model using previous campaign outcomes
3. Test different contact methods for different demographics
4. A/B test optimal timing within high-conversion months

## 📊 Project Structure
Bank-Marketing-Analysis/
│
├── README.md
├── bank-full.csv                    # Dataset
├── Bank_Marketing_Dashboard.pbix    # Power BI file
├── SQL_Queries/
│   ├── conversion_analysis.sql
│   ├── segment_performance.sql
│   └── contact_optimization.sql
└── Screenshots/
└── dashboard_preview.png
## 🎓 Skills Demonstrated
- SQL query writing and optimization
- Exploratory Data Analysis (EDA)
- Power BI dashboard development
- DAX measure creation
- Statistical analysis and interpretation
- Business insight generation
- Data-driven recommendation formulation

## 📧 Contact
Avinash Nannapaneni
- LinkedIn: [linkedin.com/in/avinash-nannapaneni-526851302](https://www.linkedin.com/in/avinash-nannapaneni-526851302)
- Email: avinashnannapaneni08@gmail.com
- GitHub: [github.com/Avinash891](https://github.com/Avinash891)

---

⭐ If you found this analysis helpful, please star this repository!


