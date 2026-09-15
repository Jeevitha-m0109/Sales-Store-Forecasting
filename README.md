# Sales-Store-Forecasting
nteractive retail sales forecasting dashboard built with React, TypeScript, and machine learning. Analyzes store/category performance, seasonal trends, promotions and holidays, compares Linear Regression and Time-Series models, and generates 1–30 day sales forecasts.
#  Store Sales Forecasting & Analytics

An interactive **Retail Store Sales Forecasting and Analytics Dashboard** built with **React, TypeScript, Vite, and machine learning techniques**.

The application analyzes historical retail sales data, identifies sales trends and patterns, compares forecasting models, and generates future sales predictions for individual stores and product categories.

---

##  Project Overview

The **Store Sales Forecasting** project is designed to help retailers understand historical sales performance and predict future demand.

The application provides:

*  Sales analytics and trends
*  Store-wise performance analysis
*  Product category analysis
*  Monthly and daily sales trends
*  Seasonal sales analysis
*  Day-of-week analysis
*  Promotion impact analysis
*  Holiday impact analysis
*  Machine learning-based forecasting
*  Model performance comparison
*  1, 7, 14, and 30-day sales forecasting
*  Forecast and analytics reports
*  CSV dataset processing

---

##  Key Features

### 1.  Sales Dashboard

The dashboard provides an overview of the complete sales dataset, including:

* Total sales
* Average daily sales
* Highest and lowest sales
* Total quantity sold
* Number of stores
* Number of product categories
* Median sales
* Latest sales information

Interactive charts make it easier to identify important business trends.

---

### 2.  Store Performance Analysis

The application evaluates individual store performance using:

* Total sales
* Average sales
* Maximum sales
* Minimum sales
* Total quantity sold
* Number of records
* Store ranking

Stores are automatically ranked according to their total sales performance.

---

### 3. Product Category Analysis

Sales performance can be analyzed across product categories such as:

* Groceries
* Electronics
* Apparel
* Home & Kitchen

The system calculates total revenue, average sales, quantity sold, record count, and category ranking.

---

### 4.  Time-Based Analysis

The application extracts several calendar features from sales dates:

* Year
* Month
* Week
* Day
* Day of week
* Quarter
* Weekend indicator
* Season

This allows the application to identify seasonal and weekly sales patterns.

---

### 5. Promotion Analysis

The system compares sales during:

* Promotional periods
* Non-promotional periods

It calculates the difference in average sales and determines the estimated promotional sales lift.

---

### 6.  Holiday Analysis

Sales during holidays are compared with regular trading days to understand the impact of holidays on retail demand.

---

##  Machine Learning & Forecasting

The project implements two forecasting approaches.

### Linear Regression

A regularized **Ridge Linear Regression** model is implemented using historical sales features.

The model uses features such as:

* Previous sales
* Quantity
* Promotion
* Holiday
* Month
* Day of week
* Quarter
* Weekend indicator
* Lag features
* Rolling averages
* Store encoding
* Product category encoding
* Season encoding

The model uses L2 regularization to improve stability and reduce overfitting.

---

### Time-Series Forecasting

A custom time-series forecasting model combines:

* Historical sales level
* Time trend
* Day-of-week seasonality
* Monthly seasonality
* Promotion effects
* Holiday effects
* Lagged sales
* Rolling averages

The model creates separate parameters for individual **store + product-category combinations**, with global parameters available as a fallback.

---

##  Data Leakage Prevention

The project takes several steps to reduce data leakage during model training.

### Chronological Train/Test Split

Instead of randomly shuffling the dataset, the records are divided chronologically:

**80% → Training Data**

**20% → Test Data**

This better represents a real-world forecasting scenario where future data should not be available during training.

### Historical Lag Features

Lag and rolling features are calculated using only previous observations.

The current record's sales value is not included in its own lag or rolling calculation.

### Training-Only Feature Scaling

Feature encoders and scaling statistics are constructed from the training dataset before evaluating the test dataset.

---

##  Model Evaluation

The forecasting models are evaluated using:

* **MAE — Mean Absolute Error**
* **MSE — Mean Squared Error**
* **RMSE — Root Mean Squared Error**
* **R² — R-Squared**

The application compares the forecasting models and selects the model with the lower test RMSE.

---

##  Sales Forecasting

Users can generate forecasts by selecting:

* Store
* Product category
* Forecast date
* Forecasting model
* Forecast horizon

Supported forecast horizons:

* **1 Day**
* **7 Days**
* **14 Days**
* **30 Days**

The forecast output includes:

* Daily predicted sales
* Average daily sales
* Total forecasted sales
* Lower estimate
* Upper estimate
* Previous sales
* Estimated quantity
* Promotion information
* Holiday information
* Seasonal information
* Historical sales context

---

##  Analytics & Visualizations

The dashboard includes visual components for:

* Sales trends
* Forecast charts
* Forecast tables
* Store performance
* Category performance
* Model metrics
* Residual analysis
* Sales details
* Forecast performance

Charts are implemented using **Recharts**.

---

##  Automated Insights

The application generates dynamic business insights based on the analyzed data.

Examples include:

* Top revenue-generating store
* Dominant product category
* Peak sales season
* Highest-demand weekday
* Promotional revenue lift
* Holiday trading impact
* Best-performing forecasting model
* Forecasted sales outlook

---

##  Project Structure

```text
store-sales-forecasting/
│
├── public/
│   └── data/
│       └── store_sales.csv
│
├── scripts/
│   └── generate_dataset.js
│
├── src/
│   ├── components/
│   │   ├── Sidebar.tsx
│   │   ├── Header.tsx
│   │   ├── Dashboard.tsx
│   │   ├── ChartCard.tsx
│   │   ├── ForecastChart.tsx
│   │   ├── ForecastTable.tsx
│   │   ├── ForecastForm.tsx
│   │   ├── ForecastResult.tsx
│   │   ├── ModelMetrics.tsx
│   │   ├── ResidualChart.tsx
│   │   └── ...
│   │
│   ├── ml/
│   │   ├── preprocessing.ts
│   │   ├── timeFeatures.ts
│   │   ├── lagFeatures.ts
│   │   ├── encoding.ts
│   │   ├── linearRegression.ts
│   │   ├── timeSeriesForecast.ts
│   │   └── modelTraining.ts
│   │
│   ├── services/
│   │   └── dataset.ts
│   │
│   ├── utils/
│   │   ├── metrics.ts
│   │   ├── salesAnalysis.ts
│   │   ├── forecastUtils.ts
│   │   ├── insights.ts
│   │   └── reportGenerator.ts
│   │
│   ├── pages/
│   │   ├── Dashboard.tsx
│   │   ├── SalesForecast.tsx
│   │   ├── SalesAnalysis.tsx
│   │   └── ForecastPerformance.tsx
│   │
│   ├── App.tsx
│   ├── main.tsx
│   ├── index.css
│   └── types.ts
│
├── .env.example
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

---

##  Dataset

The included dataset is:

`public/data/store_sales.csv`

### Dataset Information

| Property           |               Value |
| ------------------ | ------------------: |
| Total Records      |               5,856 |
| Time Period        | Jan 2024 – Dec 2024 |
| Stores             |                   4 |
| Product Categories |                   4 |
| Features           |                  10 |

### Dataset Columns

| Column             | Description                         |
| ------------------ | ----------------------------------- |
| `sales_id`         | Unique sales transaction identifier |
| `date`             | Sales date                          |
| `store_id`         | Store identifier                    |
| `product_category` | Product category                    |
| `quantity`         | Quantity sold                       |
| `previous_sales`   | Previous sales value                |
| `promotion`        | Promotion indicator                 |
| `holiday`          | Holiday indicator                   |
| `season`           | Season                              |
| `sales`            | Sales/revenue value                 |

---

## Technologies Used

### Frontend

* React
* TypeScript
* Vite
* Tailwind CSS
* Recharts
* Lucide React
* Motion

### Machine Learning / Data Processing

* TensorFlow.js
* Custom Linear Regression implementation
* Time-Series Forecasting
* PapaParse
* Statistical evaluation metrics

### Reporting

* jsPDF
* html2canvas

### Development

* Node.js
* TypeScript
* Vite

---

##  Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/store-sales-forecasting.git
```

### 2. Navigate to the Project

```bash
cd store-sales-forecasting
```

### 3. Install Dependencies

```bash
npm install
```

### 4. Start the Development Server

```bash
npm run dev
```

The application will be available through the local Vite development server.

---

##  Build for Production

```bash
npm run build
```

To preview the production build:

```bash
npm run preview
```

---

##  Type Checking

Run the TypeScript compiler without generating output:

```bash
npm run lint
```

---

##  Forecasting Workflow

```text
Raw Sales Dataset
       ↓
CSV Validation
       ↓
Data Cleaning & Preprocessing
       ↓
Calendar Feature Engineering
       ↓
Lag & Rolling Feature Generation
       ↓
Categorical Encoding & Scaling
       ↓
Chronological 80/20 Train-Test Split
       ↓
 ┌───────────────────────┐
 │                       │
 ▼                       ▼
Linear Regression   Time-Series Model
 │                       │
 └───────────┬───────────┘
             ↓
       Model Evaluation
             ↓
      RMSE / MAE / MSE / R²
             ↓
       Best Model Selection
             ↓
      Future Sales Forecast
             ↓
      Dashboard & Reports
```

---

##  Project Objectives

The main objectives of this project are to:

1. Analyze historical retail sales data.
2. Identify store and product performance.
3. Discover seasonal and weekly sales patterns.
4. Measure promotion and holiday effects.
5. Engineer meaningful time-series features.
6. Train and compare forecasting models.
7. Evaluate models using standard regression metrics.
8. Predict future sales demand.
9. Present results through an interactive dashboard.
10. Generate useful insights for retail decision-making.

---

##  Future Improvements

Possible future enhancements include:

* Advanced models such as XGBoost, Random Forest, or LSTM
* Hyperparameter optimization
* More sophisticated confidence intervals
* Real-time database integration
* User authentication
* Cloud deployment
* Automated model retraining
* Multi-year datasets
* Inventory optimization
* Demand-based stock recommendations
* Automated email/report delivery

---

##  Author

**Your Name**

GitHub: `https://github.com/your-username`

---

## If You Like This Project

If this project helped you or you found it interesting, consider giving the repository a ⭐ star on GitHub.
