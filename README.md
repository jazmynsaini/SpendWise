# SpendWise — AI Personal Financial Copilot

> **Tracking tells you what happened. SpendWise helps you decide what happens next.**

SpendWise is an AI Personal Financial Copilot designed to help users understand everyday spending, plan recurring obligations, save toward goals, and make better financial decisions.

The core idea is simple: most people can see their transactions, but fewer can see the **next best financial action**.

---

## 1. Problem Statement

### What is the problem?

Money leaves people's hands through UPI, cards, cash, bills, subscriptions, and small daily purchases. Although users can often see individual transactions, those transactions do not automatically become a clear financial plan.

The deeper problem is therefore not only **expense tracking**. It is the lack of contextual guidance connecting:

- current income
- essential and recurring expenses
- day-to-day spending behavior
- savings
- financial goals
- upcoming commitments

### Who experiences it?

The problem is relevant to everyday earners and students/young adults who manage recurring expenses, discretionary spending, savings, and personal goals.

### Why is it a problem?

Without a connected view of their finances, users may:

- lose track of category-wise spending
- miss or feel unprepared for recurring obligations
- spend money intended for savings or goals
- struggle to decide whether a large purchase is affordable
- react to overspending after it happens instead of planning ahead

### Problem statement

**People can see where their money went, but they often lack the context to decide where their money should go next.**

SpendWise addresses this missing decision layer.

---

## 2. Existing Solutions

Conventional expense-tracking and budgeting applications are useful for recording and visualizing financial history.

Typical capabilities include:

- transaction lists
- spending categories
- charts and summaries
- budgets

### Limitation / gap

These tools primarily answer:

> **"What happened?"**

SpendWise focuses on the next question:

> **"Given what happened, what should I do next?"**

The proposed difference is contextual guidance based on the user's behavior, obligations, savings, and goals.

---

## 3. Proposed Solution

SpendWise creates **one financial picture across expenses, recurring commitments, savings, and goals**.

The product works as a decision layer for everyday money:

**Income → Reserve essentials → Understand spending → Fund goals → Stay on track**

The system combines deterministic financial calculations with AI-assisted explanations and recommendations.

### Example

A user asks:

> **"Can I buy a ₹75,000 laptop?"**

Instead of returning only a generic yes/no answer, SpendWise can use the user's income, fixed expenses, savings, goals, upcoming expenses, and spending behavior to provide an illustrative recommendation such as:

> **"January would be safer than November. Saving ₹12,500 per month and reducing discretionary spending by approximately ₹2,000 per month could help you reach the goal without affecting essentials."**

The figures are illustrative and are not presented as guaranteed financial advice.

---

## 4. Key Features

### 4.1 Expense Categorization
Users can record payments and categorize them across areas such as:

- Food
- Grocery
- Travel
- Transport
- Shopping
- Education
- Healthcare
- Entertainment
- Household
- Other

This converts individual payments into useful spending signals and category patterns.

### 4.2 Recurring Expense Planner
Users can track monthly and yearly commitments.

**Monthly examples:**
- Rent
- EMI
- Electricity
- Internet
- Subscriptions
- Insurance

**Yearly examples:**
- College fees
- Health insurance
- Vehicle insurance
- Annual subscriptions

The system provides reminders so users can plan ahead.

### 4.3 Income Allocation & Safe-Spending Guidance
SpendWise separates income into meaningful buckets such as:

- essential/fixed expenses
- recommended savings
- goal contribution
- flexible/personal spending

For example, an illustrative ₹60,000 monthly income can be converted into a plan rather than treated as one amount available to spend.

### 4.4 Money Locker
Money Locker is a wallet-style behavioral savings feature.

Users can set aside money toward a goal for:

- 15 days
- 1 month
- 3 months
- 6 months
- custom duration

The purpose is to make the savings commitment visible and deliberate and reduce impulse spending.

**Important:** this is a conceptual behavioral product feature, not a regulated deposit or payment product.

### 4.5 AI Financial Copilot
Users can ask natural-language financial questions.

The AI explains the reasoning behind recommendations using structured financial context such as:

- income
- fixed expenses
- savings
- goals
- upcoming expenses
- historical spending behavior

The AI is intended to explain and personalize decisions rather than replace the underlying financial calculations.

### 4.6 Proactive Guidance
SpendWise can provide guidance around:

- safe spending
- recurring obligations
- goal progress
- major purchases
- changes in spending behavior

---

## 5. Technical Approach

### 5.1 High-Level Architecture

```text
                    ┌──────────────────────┐
                    │     Flutter App      │
                    │      Android/iOS     │
                    └──────────┬───────────┘
                               │
                 ┌─────────────┴─────────────┐
                 │                           │
        ┌────────▼────────┐       ┌──────────▼─────────┐
        │ Firebase Auth   │       │    Firestore       │
        │ Email/Phone/OTP │       │ User financial     │
        └─────────────────┘       │ data & goals       │
                                  └──────────┬──────────┘
                                             │
                                  ┌──────────▼──────────┐
                                  │ Financial Decision  │
                                  │ Engine              │
                                  │                    │
                                  │ Allocation          │
                                  │ Recurring expenses  │
                                  │ Safe spending       │
                                  │ Goal calculations    │
                                  └──────────┬──────────┘
                                             │
                                  ┌──────────▼──────────┐
                                  │ AI Guidance Layer   │
                                  │ Context + reasoning │
                                  └──────────┬──────────┘
                                             │
                                  ┌──────────▼──────────┐
                                  │ Recommendations &   │
                                  │ Alerts              │
                                  └─────────────────────┘
```

### 5.2 Data Flow

1. User authenticates using supported email/phone/OTP flows.
2. User provides financial profile information and recurring commitments.
3. User records payments and assigns categories.
4. Financial data is stored against the authenticated user.
5. The financial decision engine calculates allocations, available flexible spending, goal contributions, and relevant planning outputs.
6. The AI layer receives structured context and explains recommendations in natural language.
7. The app presents insights, reminders, and decision guidance.

### 5.3 Financial Calculation Approach

The core financial calculations should remain deterministic and auditable.

A simplified planning model is:

```text
Available Income
    - Essential / Fixed Expenses
    - Recommended Savings
    - Goal Contribution
    = Flexible / Personal Spending Capacity
```

The AI should explain the results rather than independently inventing financial numbers.

### 5.4 AI Methodology

The AI layer can use structured user context to answer questions such as:

- Can I afford this purchase?
- When would be a safer month to buy it?
- How much should I reduce discretionary spending?
- How could this purchase affect my goal?

Recommendations should be based on calculated financial context and clearly state assumptions.

### 5.5 APIs / External Services

Initial product architecture:

- Firebase Authentication
- Cloud Firestore
- AI model/API for natural-language financial guidance

Future integrations may include authorized financial/payment providers for transaction synchronization or payment execution.

**Automatic payment execution is a future capability and requires appropriate integrations and user authorization.**

### 5.6 Security Considerations

- Do not store banking passwords.
- Do not store UPI PINs.
- Use authenticated user access to financial records.
- Apply Firestore security rules so users can access only authorized data.
- Use encrypted communication through platform/provider security.
- Minimize collection of sensitive information.
- Treat AI guidance as decision support, not guaranteed financial advice.

---

## 6. Technology Stack

```text
Frontend:       Flutter / Dart
Platforms:      Android + iOS
Authentication: Firebase Authentication
Database:       Cloud Firestore
Backend Logic:  Firebase / server-side functions as required
AI Layer:       AI model/API for contextual financial guidance
Architecture:   Deterministic financial engine + AI explanation layer
Version Control: Git + GitHub
```

The current prototype is being developed as a Flutter mobile application and has Firebase initialized for the project.

---

## 7. Expected Impact

### Who benefits?

- Students and young adults learning to manage money
- Salaried users managing monthly income and obligations
- Users saving toward specific purchases or goals
- Anyone who wants more context than a transaction history provides

### How does SpendWise improve the current situation?

Instead of making users look backward at isolated transactions, SpendWise helps them connect:

**spending → obligations → savings → goals → next decision**

This can help users:

- become more aware of spending patterns
- prepare for recurring expenses
- build intentional saving behavior
- make large purchases more thoughtfully
- reduce avoidable impulse spending

### Potential long-term value

If successfully implemented and integrated with appropriate financial services, SpendWise could become a personalized decision-support layer for everyday financial planning.

---

## 8. Future Scope

### Financial integrations
- Authorized bank/payment integrations
- Transaction synchronization
- Subscription detection
- Authorized payment execution

### Smarter planning
- More advanced forecasting
- Personalized goal timelines
- Spending anomaly detection
- Improved affordability analysis

### Broader use cases
- Family/shared goals
- Household financial planning
- Multiple financial profiles
- More financial categories and use cases

### AI improvements
- More contextual financial conversations
- Multilingual assistance
- Voice-based financial queries
- More transparent recommendation explanations

---

## Feasibility & Limitations

SpendWise is designed to be feasible in stages.

### MVP / prototype scope

The first version can focus on:

- authentication
- manual expense recording and categorization
- recurring expense planning
- income allocation
- goal tracking
- Money Locker as a behavioral feature
- AI question-and-answer experience using structured financial data

### Limitations

The prototype does not claim to be a bank, payment processor, or regulated financial institution.

Real banking/payment integrations, automatic payment execution, and actual custody/locking of funds require appropriate third-party integrations, authorization, security controls, and regulatory compliance.

AI recommendations are decision-support outputs based on user-provided information and calculations, not guaranteed financial advice.

---

## Evaluation Criteria Alignment

| Evaluation Criterion | How SpendWise Addresses It |
|---|---|
| **Problem Understanding** | Identifies the gap between seeing transactions and knowing what financial action to take next. |
| **Problem Relevance** | Targets a common everyday problem: fragmented spending, recurring obligations, saving, and purchase decisions. |
| **Innovation** | Adds a decision layer combining financial context, proactive guidance, major-purchase planning, AI reasoning, and behavioral savings. |
| **Technical Approach** | Flutter mobile application with Firebase, structured financial calculations, and an AI guidance layer. |
| **Feasibility** | MVP can work with user-entered data; regulated banking/payment capabilities are explicitly treated as future integrations. |
| **Impact** | Helps users understand spending, plan obligations, save intentionally, and make better purchase decisions. |
| **Clarity** | The concept is summarized by one distinction: **tracking tells you what happened; guidance helps decide what happens next.** |

---

## One-Line Pitch

> **SpendWise is an AI Personal Financial Copilot that turns everyday financial data into personalized, actionable decisions.**

## Closing

> **Know where your money goes.  
> Know where it should go.  
> Make every rupee count.**
