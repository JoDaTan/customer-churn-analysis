# Customer Churn Analysis
A data-driven analysis of customer churn patterns for a music streaming service, uncovering critical retention drivers and providing actionable recommendations to reduce churn by 40%.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Recommendations](#recommendations)
- [Technologies Used](#technologies-used)
- [Acknowledgement](#acknowledgement)

## Project Overview
This project analyzes customer churn for a subscription-based music streaming platform. Using behavioral data and subscription patterns from March-June 2023, the analysis identifies why customers leave and what drives long-term retention.

**Business Context:**
- 30 customers across Basic ($2.99) and Premium ($9.99/$7.99 discounted) tiers
- Overall churn rate: 43%
- Subscription period: March - June 2023
- Customer engagement: Basic (3 active days), Premium (2.5 days), Discounted Premium (2 days)

**Key Discovery:** Customers who reach 4 active days have 0% churn, but only 17% of customers achieve this threshold.

## Dataset
- `maven_music_customers.csv` - customer demographics, subscription plans, join and cancel dates, pricing
- `listen_history.csv` - Individual audio plays per session
- `audio_info.csv` - Song/podcast metadata (genre, popularity)
- `sessions.csv` - Login timestamps

## Methodology
### 1. Data Preparation
- converted date columns to datetime format
- converted string data (Subscription rate) to numeric
- handled missing values in Cancellation Date, Discount
- Validated data quality

### 2. Feature Engineering
- Churn Status: 1 - churned, 0 - active
- Active Days: count of unique days with listening activity
- Join month

### 3. Exploratory Data Analysis
- Customer segmentation by Subscription plan & Discount
- Cohort analysis by join month
- Subscription plan performance
- Distribution of churn and customer engagement
- Correlation analysis of churn drivers

## Key Findings
### 1. **Cohort Performance Varies Significantly**
- March subscribers: 31% churn (best performing)
- April subscribers: 38% churn
- May subscribers: 67% churn (worst performing)

### 2. **Subscription Plan Performance and Churn Rate**
- Basic (Ads): 24% churn rate
- Premium (No Ads): 69% churn rate
- Discounted Premium (No Ads): 86% churn rate
- Discounts increases churn by 17% percentage points

### 3. **Day 4 is the Magic Retention Threshold**
- Customers with **4+ active days**: 0% churn
- Customers with **1-3 active days**: 36 - 80% churn
- **Only 17% of customers reach 4 active days** (critical opportunity)

| Active Days | Churn Rate | Customer Count |
|-------------|------------|----------------|
| 1 day       | 80.0%      | 5              |
| 2 days      | 55.6%      | 9              |
| 3 days      | 36.4%      | 11             |
| 4+ days     | 0.0%       | 5              |

### 4. **Strongest Churn Predictors (Correlation Analysis)**
- Active Days: **r = -0.46** (strongest behavioral predictor)
- Discount Status: **r = +0.47** (discounts predict churn)
- Subscription Plan: **r = +0.46** (Premium predicts higher churn)

## Recommendations
### 1. Solve the Day 4 Activation Problem (Highest Impact)
**Actions:**
- **Day 1-3 Onboarding Campaign**: Make the come back
  - **Day 1**: Help new subscribers find songs they love right away. Show them 3 great songs immediately.
  - **Day 2**: Send them a message: "We found 10 songs you'll love!"
  - **Day 3**: Tell them: "You're on a 3-day streak! Come back tomorrow!"
  - **Day 4+**: Celebrate: "You're a power user!"

- **Make the app easy:**
  - When they open the app, play music automatically (no searching needed)
  - Show them playlists like "Start Here" instead of showing everything 
  - Remove any barriers in the first 3 days
  - Gamify their experience with streak counters, milestone celebrations

### 2. No More Discounts to New Customers
Since customers with discounts leave 86% of the time. They only signed up for the cheap price. So,
  - No more automatic discounts for new Premium customers
  - No permanent price cuts

Instead,
  - Only give discounts to people who already use the app a lot (4+ days)
  - Give discounts to Basic users who've been active for 7 days: "Upgrade and get 30% off for 3 months"
  - Offer free trials instead: "Try Premium free for 14 days"

### 3: Make Premium Worth the Money
Premium users pay 3x more but use the app LESS than Basic users. They don't see the value.
**Actions:**
- **Add more Premium benefits:**
  - Exclusive content (behind-the-scenes with artists)
  - Get new music before everyone else
  - Special playlists made by experts
  - See what your friends are listening to
  - Connect with artists (Q&As, meet & greets)

- **Show customers what they're getting:**
  - Send monthly email: "You listened to 500 songs ad-free this month. That's worth $50 (you paid only $9.99)!"
  - When Basic users see a cool feature, say: "Get this with Premium"

- **Wait before offering Premium:**
  - Don't push Premium on Day 1
  - Wait until they've used the app 4+ times
  - Then say: "You're a great listener! Try Premium free for 7 days"

### Priority 4: Catch Customers Before They Leave
Notice when people stop using the app.

**Actions:**
- **Find people at risk:**
  - Used the app only 1-3 times
  - Haven't come back in 3+ days

- **Reach out to them: (Duolingo style)**
  - Day 4 not back: "We miss you! Here's a playlist just for you"
  - Day 7 not back: Offer personal help to find music they'll love
  - Day 14 not back: Ask "What can we do better?" + give them something special

- **Reward loyal users:**
  - If someone uses the app 7+ times: "You're in our top 5%! Here's a VIP badge"
  - Give them special perks
  - Let them invite friends for rewards

## Technologies Used
  - **Python 3.13**
  - **Pandas** - Data manipulation and merging
  - **NumPy** - Numerical operations
  - **Matplotlib** - Data visualization
  - **Seaborn** - Statistical plots
  - **Jupyter Notebook** - Interactive analysis

## Acknowledgement
Dataset provided by [Maven Analytics](https://mavenanalytics.io/). This analysis demonstrates real-world subscription business challenges and data-driven decision making.
