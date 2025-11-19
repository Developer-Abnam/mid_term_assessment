# Buenos Aires Real Estate Price Prediction

## 📋 Project Overview
This project analyzes real estate data from Buenos Aires to build a machine learning model that predicts apartment prices. The model helps estimate property values based on features like size, location, and neighborhood.

## 🎯 Project Goals
- Clean and prepare Buenos Aires real estate data
- Explore relationships between apartment features and prices
- Build a predictive model for apartment prices
- Create a tool to estimate property values

## 📊 Dataset Information
The dataset contains property listings from Buenos Aires with various features including:
- Property type and location details
- Size measurements (square meters)
- Geographic coordinates (latitude/longitude)
- Price information in USD

## 🔧 Data Processing Steps

### Data Cleaning & Filtering
- **Location Filter**: Only properties in "Capital Federal" (Buenos Aires city)
- **Property Type**: Focused only on apartments
- **Price Range**: Limited to properties under $400,000 USD
- **Outlier Removal**: Removed extreme values in apartment sizes (keeping middle 80%)

### Feature Engineering
- **Split Coordinates**: Separated "lat-lon" into individual latitude and longitude columns
- **Neighborhood Extraction**: Parsed location data to extract neighborhood names
- **Column Removal**: Eliminated irrelevant, redundant, or leaky features including:
  - High null-value columns (`floor`, `expenses`)
  - Low/high cardinality columns
  - Leaky features (various price columns that would reveal the answer)
  - Collinear features (`surface_total_in_m2`, `rooms`)

## 📈 Exploratory Data Analysis

### Apartment Size Distribution
- Analyzed the range and distribution of apartment sizes (surface area in square meters)
- Most apartments fall within a moderate size range after outlier removal

### Price vs Area Relationship
- Created scatter plots to visualize how apartment prices correlate with size
- Generally, larger apartments command higher prices, as expected

### Geographic Price Analysis
- Used interactive maps to show how prices vary across different neighborhoods
- Visualized price distribution across Buenos Aires using geographic coordinates

## 🤖 Machine Learning Model

### Baseline Model
- **Simple Approach**: Used mean apartment price as baseline prediction
- **Baseline MAE**: $45,869.27 (mean absolute error)

### Final Model Pipeline
The model uses a sophisticated processing pipeline:
1. **OneHotEncoder**: Converts categorical data (neighborhoods) to numerical format
2. **SimpleImputer**: Handles any missing values in the data
3. **Ridge Regression**: Regularized linear model to prevent overfitting

### Model Performance
- **Training MAE**: $28,380.32
- **Improvement**: 38% better than baseline model
- The model successfully learned patterns from the training data

## 🚀 How to Use the Model

The project includes a prediction function:
```python
make_prediction(area, lat, lon, neighborhood)
```

**Example:**
```python
make_prediction(110, -34.60, -58.46, "Villa Crespo")
# Returns: "Predicted apartment price: $[amount]"
```

**Parameters:**
- `area`: Apartment size in square meters
- `lat`, `lon`: Geographic coordinates
- `neighborhood`: Name of the neighborhood in Buenos Aires

## 📁 Project Structure
- **Data Cleaning**: `wrangle()` function for data preprocessing
- **EDA**: Multiple visualizations (histograms, scatter plots, maps)
- **Model Development**: Machine learning pipeline with Ridge regression
- **Prediction**: Ready-to-use function for price estimation

## 💡 Key Insights
1. **Location Matters**: Prices vary significantly across different neighborhoods
2. **Size Correlation**: Larger apartments generally cost more, but location modifies this relationship
3. **Model Effectiveness**: The Ridge regression model provides reasonable price estimates with a $28,380 average error

## 🔮 Potential Improvements
- Include more features if available
- Try different algorithms (Random Forest, Gradient Boosting)
- Incorporate temporal trends in real estate prices
- Add more granular location features

This project demonstrates a complete data science workflow from data cleaning to deploying a functional prediction tool for Buenos Aires real estate markets.