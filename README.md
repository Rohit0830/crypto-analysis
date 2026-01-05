# Crypto Market Analysis and Prediction

## Project Overview
This project focuses on analyzing cryptocurrency market data to identify price trends, trading volume behavior, volatility, and overall market performance.  
Using Power BI, DAX measures, and analytical calculations, the project provides interactive visual insights along with basic trend-based predictions.

This project is created for educational and analytical purposes only and does not represent financial advice.

---

## Objectives
- Analyze historical cryptocurrency price data  
- Identify trends and volatility patterns  
- Create interactive dashboards and visual reports  
- Implement DAX measures for advanced analysis  
- Perform return, growth, and trend calculations  
- Generate basic predictive insights using historical data  

---

## Dataset Information
- Source: https://www.coingecko.com/en/api
- Cryptocurrencies: Bitcoin, Ethereum, and other major coins
- Time Period: live data
- Attributes:
  - Date  
  - Open, High, Low, Close prices  
  - Trading Volume  
  - Market Capitalization  

---

## Tools and Technologies
- Power BI – Data modeling and visualization  
- DAX (Data Analysis Expressions) – Measures and calculations  
- Excel / CSV – Data cleaning and preprocessing  
- Git and GitHub – Version control and project sharing  

---

## Data Modeling
- Created a dedicated Date Table for time-intelligence analysis  
- Established relationships between date, price, and volume tables  
- Optimized the data model for performance and accuracy  

---

## Visualizations
The following visualizations were created using Power BI:
- Price trend line charts  
- Trading volume bar charts  
- Moving averages (7-day ago and 7-day ahead)  
- Monthly and yearly performance analysis  
- Market comparison and distribution charts  

Dashboard screenshot is available in the Result folder.

---

## DAX Measures
Key DAX measures implemented in this project include:
- Total Trading Volume  
- Average Closing Price  
- Daily Return Percentage  
- Monthly Growth Rate  
- Moving Averages  
- Year-to-Date (YTD) Performance  

### Sample DAX Measure
```DAX
Daily Return % =
DIVIDE(
    [Close Price] - [Previous Close],
    [Previous Close]
) * 100
```

---

## Contributions

Contributions are welcome.
Feel free to fork this repository and submit pull requests for improvements.

## Contact

Author: Rohit Kushwaha
Email: rkrohit3008@gmail.com