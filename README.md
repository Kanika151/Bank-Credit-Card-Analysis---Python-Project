# Bank Credit Card Data Analysis

### Dashboard SnapShot : 

![DDashboard SnapShot : 

![Dashboard_upload](https://github.com/Kanika151/Bank-Credit-Card-Analysis---Python-Project/blob/main/20240828_195012_0000.png) 


## Project Overview
This project involves analyzing a bank credit card dataset to gain insights into customer behavior, financial performance, and the impact of various factors on key metrics. The analysis includes visualizations created using Python, `pandas`,`matplotlib`, 'seaborn'.

## Dataset Description

The project uses two datasets:
- **Customer Details (`cust`)**: Contains information about the customers.
- **Credit Card Details (`cc`)**: Contains information about the customers' credit card usage.

### `cust` Table Columns:
- `Client_Num` (Unique ID): Unique identifier for each customer.
- `Customer Age`: Age of the customer.
- `Dependent Count`: Number of dependents the customer has.
- `Education Level`: Customer's education level.
- `Marital Status`: Marital status of the customer.
- `Car Owner`: Whether the customer owns a car (Yes/No).
- `House Owner`: Whether the customer owns a house (Yes/No).
- `PersonalLoan`: Whether the customer has a personal loan (Yes/No).
- `Customer Job`: The employment status of the customer (Business/Employed).
- `Income`: Customer's annual income.
- `Customer Satisfaction Score`: Customer's satisfaction score out of 5.

### `cc` Table Columns:
- `Client ID` (Primary Key): Unique identifier for each customer.
- `Card Category`: Type of card held by the customer (Blue, Platinum, Gold, Silver).
- `Activation 30 Days`: Binary indicator (0 or 1) showing whether the card was activated within 30 days.
- `Customer Acquisition Cost`: Cost incurred by the bank to acquire the customer.
- `Quarter`: Financial quarter during which the data was recorded.
- `Current Year Credit Limit`: Credit limit assigned to the customer for the current year.
- `Total Revolving Balance`: Total balance that is carried from one billing cycle to the next.
- `Total Transaction Amount`: Total amount spent using the card.
- `Total Transaction Volume`: Number of transactions made.
- `Avg Utilization Ratio`: Average ratio of the credit limit that is utilized.
- `Use Chip`: Binary indicator (0 or 1) showing whether the card has chip usage.
- `Expenditure Type`: Category of the expenditure (e.g., Travel, Shopping).
- `Interest Earned`: Interest earned by the bank on the revolving balance.
- `Total Revenue`: Total revenue generated from the customer, calculated as `Annual Fees + Interest Earned + Total Transaction Amount`.

## Visualizations

The project includes the following key visualizations:

1. **Customer Category Distribution** (Bar/Pie Chart)
2. **Gender Distribution Across Card Categories** (Stacked Bar Chart)
3. **Activation Rate within 30 Days by Category and Gender** (Grouped Bar Chart)
4. **Customer Acquisition Cost by Category** (Box Plot/Bar Chart)
5. **Current Year Credit Limit Distribution** (Histogram)
6. **Total Revolving Balance by Category** (Box Plot/Bar Chart)
7. **Total Transaction Amount vs. Total Transaction Volume** (Scatter Plot)
8. **Average Utilization Ratio by Category** (Bar Chart)
9. **Chip Usage Rate by Category and Gender** (Stacked Bar Chart/Pie Chart)
10. **Expenditure Type Distribution** (Pie/Bar Chart)
11. **Interest Earned by Category** (Bar Chart)
12. **Total Revenue by Category** (Bar Chart/Box Plot)
13. **Quarterly Total Revenue Trend** (Line Chart)
14. **Interest Earned vs. Total Revolving Balance** (Scatter Plot)
15. **Correlation Matrix** (Heatmap)

## Dependencies

To run this project, you will need the following Python packages:
- `pandas`
- `matplotlib`
- `seaborn`

You can install these packages using pip:

bash
pip install pandas matplotlib seaborn


# Running the Project

1. Load the Data:

Ensure the cust and cc datasets are loaded into pandas DataFrames.

2. Merge Datasets:

Use the Client_Num column from the cust table and the Client ID column from the cc table to merge the DataFrames where necessary, especially for visualizations that require data from both tables.

3. Generate Visualizations:

Run the provided Python code to generate the visualizations. Each code snippet corresponds to one of the visualizations listed above.

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Example: Loading data
cust = pd.read_csv('customer_details.csv')
cc = pd.read_csv('credit_card_details.csv')

# Merging the DataFrames
merged_df = pd.merge(cc, cust[['Client_Num', 'Gender']], left_on='Client ID', right_on='Client_Num')

# Generating a chart
activation_rate = merged_df.groupby(['Card Category', 'Gender'])['Activation 30 Days'].mean().unstack()
activation_rate.plot(kind='bar', color=['lightcoral', 'skyblue'])
plt.title('Activation Rate within 30 Days by Category and Gender')
plt.xlabel('Card Category')
plt.ylabel('Activation Rate')
plt.show()

4.Customization:
You can customize the plots further by adjusting colors, labels, and other settings in the code.


# Conclusion
This project provides a detailed analysis of bank credit card usage patterns, customer behavior, and financial performance through various visualizations. The insights gained can help inform decisions on customer segmentation, marketing strategies, and risk management.
