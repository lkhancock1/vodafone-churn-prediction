# Vodafone Customer Churn Prediction & Personalised Retention Emails

This project uses machine learning and generative AI to identify Vodafone customers at risk of churning and generate personalised, brand-aligned retention emails.

---

## Overview

The solution combines two key components:

1. **Churn Prediction**  
   An XGBoost model predicts the probability of churn for each customer. SHAP values are used to explain individual predictions and highlight the top contributing factors. A Logistic Regression model has been used for baseline performance and easy interpretability.

2. **Email Generation**  
   A Google Gemini LLM generates customer-specific retention emails. The prompt is tailored using churn probability, customer profile, and SHAP explanations, while adhering to Vodafone’s tone of voice.

---

## Project Structure

```
.
├── src/
│   ├── Vodafone_Churn_Model.py     # Clean, single script complying with PEP8 guidelines
│
├── data/
│   └── Vodafone_Customer_Churn_Sample_Dataset.csv
│
├── notebooks/
│   ├── Vodafone_Churn_Notebook.py  # More rough, notebook format of the same script with more comments explaining thought process
│
├── README.md
```

---

## Getting Started

1. **Install dependencies**

Google Colab had requirements pre-installed so a requirements.txt file wasn't necessary in this environment.

2. **Set up your Gemini API key**

Ensure your API key is available as an environment variable.

3. **Run the pipeline**

```bash
python Vodafone_Churn_Model.py
```

---

## Features

- **Logistic Regression trained** to establish baseline performance and for easy interpretation
- **XGBoost-based churn prediction** for increased accuracy
- **SHAP explainability** to identify key churn drivers
- **LLM-generated personalised emails** with tone and structure aligned to brand guidelines
- **Prompt logic adaptations** based on churn severity, key drivers and general subscriptions

---

## Prompt Engineering

Vodafone tone of voice has been integrated into the prompt instructions, along with prompt engineering best practice and dynamic inputs

- Role based framing like "You are a friendly Vodafone customer Service rep"
- Concise instructions without repetition, rather than the entire Vodafone Tone of Voice document
- Specific instructions about structure
- Clear and specific instructions, nothing vague
- Context about the customer
- Dynamic input specific to the customer like urgency of churn risk and key churn drivers

## Sample Output

Subject: Hi [Customer Name], We've Got Something Special for You! 

Hi [Customer Name], 

We appreciate your loyalty as a Vodafone customer for the past 10 months! We're reaching out because we value your business and want to ensure you're getting the most from your Vodafone services. 

We've recently boosted our TV streaming library with loads of new shows and movies, so there's even more to enjoy. 
Our fiber optic network continues to improve, delivering even faster and more reliable speeds. 
To show our appreciation, we'd like to offer you a special discount of 15% off your monthly bill for the next 3 months! This means £14.28 off your £95.20 plan. 

To claim your 15% discount, simply reply to this email with "YES" within the next 7 days. 

Thanks for being a valued Vodafone customer!

Vodafone Customer Care Team

---

## Scaling Opportunities

This approach can be adapted to lifestage or segment, for example:

- New customer reassurance
- Triggering in campaign tools
- Upsell or cross-sell opportunities

Email tone, structure, and inputs can be modified per journey while reusing the same underlying LLM and SHAP-driven architecture.

---

## Assumptions

- SHAP values provide actionable, human-readable explanations
- Customer feature data is accurate and up to date
- Personalised messaging improves retention over generic communications
- Gemini’s LLM is suitable for producing brand-compliant content with carefully engineered prompts

---

## Next Steps

- Integrate with live customer data pipelines (e.g. Snowflake, BigQuery)
- Connect to marketing automation tools (e.g. Salesforce, Braze)
- Deploy in a batch process to identify newly at risk customers daily
- Build a dashboard to monitor churn trends and email engagement
- Run A/B tests to compare AI-generated vs traditional messaging

---

## Author

Developed by Laura Hancock  