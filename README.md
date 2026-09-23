# customer-purchase-prediction
Customer Purchase Prediction Dashboard — an interactive React/TypeScript ML application for analyzing customer behavior and predicting purchase likelihood using Logistic Regression and Random Forest.
#  Customer Purchase Prediction

An interactive machine-learning dashboard for analyzing customer behavior and predicting whether a customer is likely to make a purchase.

The application combines **customer analytics, behavioral feature engineering, machine-learning classification, model evaluation, and interactive visualizations** in a modern React + TypeScript interface.

##  Features

*  **Customer Analytics Dashboard**

  * Total customers
  * Purchase and non-purchase statistics
  * Average age and income
  * Website visits and time spent
  * Purchase-rate analysis

*  **Machine Learning Prediction**

  * Logistic Regression classifier
  * Random Forest classifier
  * Real-time purchase probability prediction
  * Configurable classification threshold

*  **Feature Engineering**

  * Engagement Score
  * Purchase History Score
  * Cart Engagement
  * Customer Value Indicator

*  **Model Evaluation**

  * Accuracy
  * Precision
  * Recall
  * F1 Score
  * ROC-AUC
  * Confusion Matrix

*  **Customer Behavior Analysis**

  * Purchase rate by age group
  * Purchase rate by income range
  * Website engagement comparisons
  * Time-spent comparisons
  * Previous-purchase analysis

*  **Data Preprocessing**

  * Input validation
  * Missing-value handling
  * Duplicate detection
  * Binary/target normalization
  * Range validation
  * Feature standardization

*  **Report Generation**

  * Generate downloadable analysis reports from the dashboard.

##  Machine Learning Pipeline

The project implements the machine-learning pipeline directly in TypeScript rather than relying on an external Python ML backend.

### 1. Data preprocessing

Customer records are validated and cleaned before being passed to the models.

The preprocessing pipeline handles:

* Numeric conversion
* Missing values
* Duplicate customer IDs
* Target normalization
* Binary feature normalization
* Range validation

### 2. Feature engineering

The application derives additional behavioral features from the original customer attributes.

#### Engagement Score

Combines:

* Website visits
* Time spent on the website
* Pages viewed

#### Purchase History Score

Represents historical purchasing activity.

#### Cart Engagement

Combines cart additions with the customer's page-view activity.

#### Customer Value Indicator

Combines income with previous purchasing behavior.

The final model feature vector contains **13 features**:

```text
age
income
website_visits
time_spent
previous_purchases
pages_viewed
cart_additions
discount_used
customer_tenure
engagementScore
purchaseHistoryScore
cartEngagement
customerValueIndicator
```

##  Models

### Logistic Regression

The project contains a custom Logistic Regression implementation using:

* Sigmoid activation
* Binary cross-entropy loss
* Gradient descent
* L2 regularization
* Standardized input features

### Random Forest

The project also implements a custom Random Forest classifier using:

* Bootstrap sampling
* Multiple decision trees
* Gini impurity
* Random feature selection
* Configurable tree depth
* Ensemble probability averaging

The current training configuration uses **24 trees** with a maximum depth of **6**.

##  Model Evaluation

The dataset is divided using an **80/20 stratified train-test split**.

```text
80% → Training
20% → Held-out testing
```

Feature scaling parameters for Logistic Regression are calculated using the training data only, helping prevent data leakage from the test set.

Models are evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* Confusion Matrix

The classification threshold can also be adjusted in the application.

##  Application Pages

### Dashboard

Provides an overview of the customer dataset with interactive charts and key statistics.

### Purchase Predictor

Enter customer information and receive:

* Purchase probability
* No-purchase probability
* Prediction
* Confidence
* Behavioral engagement score
* Model used for prediction

### Customer Analysis

Explore customer behavior and purchasing patterns across different demographic and engagement segments.

### Model Performance

Compare the two machine-learning models and inspect:

* Evaluation metrics
* Confusion matrix
* Classification threshold
* Dataset partition
* Algorithmic insights

##  Tech Stack

**Frontend**

* React
* TypeScript
* Vite
* Tailwind CSS

**Data Visualization**

* Recharts

**UI**

* Lucide React
* Motion

**Data Processing**

* PapaParse

**Machine Learning**

* Custom TypeScript Logistic Regression
* Custom TypeScript Random Forest

**Reports**

* jsPDF
* html2canvas

##  Project Structure

```text
customer-purchase-prediction/
│
├── public/
│   └── data/
│       └── customer_purchases.csv
│
├── src/
│   ├── components/
│   │   ├── ChartCard.tsx
│   │   ├── ConfusionMatrix.tsx
│   │   ├── CustomerDetails.tsx
│   │   ├── CustomerForm.tsx
│   │   ├── CustomerTable.tsx
│   │   ├── Header.tsx
│   │   ├── ModelMetrics.tsx
│   │   ├── PredictionResult.tsx
│   │   ├── ReportButton.tsx
│   │   ├── Sidebar.tsx
│   │   └── StatCard.tsx
│   │
│   ├── ml/
│   │   ├── featureEngineering.ts
│   │   ├── logisticRegression.ts
│   │   ├── modelTraining.ts
│   │   ├── preprocessing.ts
│   │   └── randomForest.ts
│   │
│   ├── pages/
│   │   ├── CustomerAnalysis.tsx
│   │   ├── Dashboard.tsx
│   │   ├── ModelPerformance.tsx
│   │   └── PurchasePredictor.tsx
│   │
│   ├── services/
│   │   └── dataset.ts
│   │
│   ├── utils/
│   │   ├── analysis.ts
│   │   ├── insights.ts
│   │   ├── metrics.ts
│   │   └── reportGenerator.ts
│   │
│   ├── App.tsx
│   ├── index.css
│   ├── main.tsx
│   └── types.ts
│
├── public/data/
│   └── customer_purchases.csv
│
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

##  Getting Started

### Prerequisites

Make sure you have:

* Node.js
* npm

### Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/customer-purchase-prediction.git
cd customer-purchase-prediction
```

Install dependencies:

```bash
npm install
```

### Run the development server

```bash
npm run dev
```

The application will be available at the local Vite development URL shown in your terminal.

### Build for production

```bash
npm run build
```

### Type-check the project

```bash
npm run lint
```

##  Dataset

The application uses a customer purchase dataset containing behavioral and demographic attributes such as:

* Age
* Gender
* Income
* Website visits
* Time spent
* Previous purchases
* Pages viewed
* Cart additions
* Discount usage
* Customer tenure
* Purchase outcome

The target variable is:

```text
purchase
```

where:

```text
1 = Purchase
0 = No Purchase
```

##  Important Note

This project is designed as an educational and demonstration application for machine-learning concepts.

The predictions should not be treated as guaranteed customer behavior. Model performance depends on the quality, size, and representativeness of the underlying dataset.

##  Project Goals

This project demonstrates how a complete machine-learning workflow can be integrated into a modern frontend application:

```text
Raw Customer Data
       ↓
Data Cleaning & Validation
       ↓
Feature Engineering
       ↓
Train/Test Split
       ↓
Model Training
   ↙          ↘
Logistic     Random
Regression   Forest
   ↘          ↙
 Model Evaluation
       ↓
Purchase Prediction
       ↓
Interactive Dashboard
```

## License

This project is available for educational and portfolio purposes.
