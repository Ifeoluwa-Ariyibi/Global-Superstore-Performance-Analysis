# Global Superstore Performance Analysis

**Description:** This project involves an in-depth analysis of Global Superstore, a global online retailer headquartered in New York. The retailer serves customers in 147 countries and offers a diverse product catalog with over 10,000 products across three main categories: office supplies, furniture, and technology. As a Data Analyst, the goal is to derive actionable insights from the Superstore dataset to help management make data-driven decisions to enhance performance and profitability.

## Table of Contents
- [About Project](#About-Project)
- [Questions](#Questions)
- [Data Cleaning and Transformation](#Data-Cleaning-and-Transformation)
- [Full DashBoard](#Full-DashBoard)
- [Recommendation](#Recommendation)

# About Project
This project centers on the analysis of Global Superstore, a New York-based global online retailer with a vast product catalog spanning over 10,000 items. Serving customers across 147 countries, Global Superstore offers a diverse range of products in three primary categories: office supplies, furniture, and technology. As a Data Analyst, the objective is to analyse the Superstore dataset to extract meaningful insights that will assist management in making strategic decisions aimed at boosting performance and profitability.

## Questions 

- Question 1.
    a) What are the three countries that generated the highest total profit for Global Superstore in 2014?
    b) For each of these three countries, find the three products with the highest total profit. What are the products’ names and the total profit for each product?
- Question 2.
    a) Identify the 3 subcategories with the highest average shipping cost in the United States.
- Question 3.
    a) Assess Nigeria’s profitability (i.e., total profit) for 2014. How does it compare to other African countries?
    b) What factors might be responsible for Nigeria’s poor performance? Investigate shipping costs and the average discount as potential root causes.
- Question 4.
    a) Identify the product subcategory that is the least profitable in Southeast Asia.
    b) Is there a specific country in Southeast Asia where Global Superstore should stop offering the identified subcategory?
- Question 5.
    a) Which city is the least profitable (in terms of average profit) in the United States? Disregard cities with less than 10 orders.
    b) Why is this city’s average profit so low?
- Question 6.
    a) Which product subcategory has the highest average profit in Australia?
- Question 7.
    a) Who are the most valuable customers and what do they purchase?


## Data Cleaning and Transformation

The project focuses on analyzing the Global Superstore dataset, which is sourced from an Excel workbook containing multiple sheets. The data includes sales records, return information, and personnel details, covering various aspects of Global Superstore’s operations across 147 countries and a diverse product catalog.

- Data Source: File:[GlobalSuperstore - Capstone.xlsx](https://github.com/user-attachments/files/16633663/GlobalSuperstore.-.Capstone.xlsx)

- Sheets:

  Orders: Contains detailed sales data with columns such as Row ID, Order ID, Order Date, Ship Date, Customer ID, Product Name, Sales, Quantity, Discount, Profit, Shipping Cost, and more.
  Returns: Includes information on returned orders with columns Returned, Order ID, and Market.
  People: Contains data on personnel and their associated regions with columns Person and Region.

- Data Preparation Steps:

  - The three sheets (Orders, Returns, and People) were merged into a single dataset to create a comprehensive view of all relevant data.
  - Order ID was used as a primary key to link data between the Orders and Returns sheets, while the Region column served as a key for integrating the People sheet with the rest of the data.

- Data Cleaning:

  - All blank rows and columns were identified and removed to ensure the dataset was clean and ready for analysis.
  - Person and Region (from the People sheet) were removed, as they were not relevant for the core analysis.
  - Order ID (after integration) and Returned columns removed, to simplify the dataset.
  - Market (duplicate column) and Postal Code were also removed, as they were not critical to the analysis.
  - Ensured all columns were properly formatted, especially dates and numerical fields, to facilitate accurate calculations and analysis.

- Column Creation:
  - Created a new column Year by extracting the year from the Order Date column. This was done using Power BI’s DAX functionality to support time-based analysis. DAX Code: Year = YEAR('Orders'[Order Date])
  - Country Rank = RANKX(ALL('Orders'[Country]),[Total Profit],,DESC, DENSE)
  - Product Rank = RANKX(ALL('Orders'[Product Name]), CALCULATE([Total Profit], ALLEXCEPT('Orders', 'Orders'[Country])),,DESC, DENSE)
  - Product Rank Country = RANKX(FILTER(ALL('Orders'[Product Name]), CALCULATE([Total Profit], ALLEXCEPT('Orders', 'Orders'[Country]))>0),CALCULATE([Total Profit]),,DESC, DENSE)
  - Total order = DISTINCTCOUNT(Orders[Order ID]).
  - Total Profit = SUM('Orders'[Profit]).

- Final Dataset:

The resulting dataset was well-structured, clean, and enriched with additional calculated columns. This prepared dataset was then used for further analysis and visualization in Power BI, enabling insightful business intelligence reports to guide strategic decision-making for Global Superstore.

## Full DashBoard
![Dashboard](https://github.com/user-attachments/assets/e4f7bfd4-b34e-476a-b5a4-aa76036bde30)

Key Highlights from the Global Superstore Dashboard

- Top Performing Countries:
  - The United States, China, and India were the top three countries by total profit in 2014, with the U.S. leading at 286.40K.
  - In the U.S., the highest-grossing products were:
      - Canon Image CLASS 2200 Advanced Copier (25.2K profit)
      - Cisco Smart Phone, Full Size (17.03K profit)
      - Motorola Smart Phone, Full Size (17.24K profit)
  
- Shipping Costs in the U.S.:
  - The subcategories with the highest average shipping costs were:
      - Copiers
      - Machines
      - Tables

- Nigeria’s Profitability:
  - Nigeria recorded a negative profit in 2014, lagging behind other African countries.
  - High shipping costs and potentially large discounts may have contributed to this poor performance.

- Southeast Asia’s Least Profitable Subcategory:
  - The Tables subcategory was the least profitable in Southeast Asia, particularly in Indonesia, with a loss of -10,680.28.
  - Global Superstore might consider discontinuing the Tables subcategory in Indonesia.

- Least Profitable U.S. City:
  - Lancaster was the least profitable city in the U.S., considering cities with at least 10 orders.

- Australia’s Top Subcategory:
  - Appliances had the highest average profit among product subcategories in Australia.

- Most Valuable Customers:
  - The most profitable customers preferred purchases in the Furniture, Office Supplies, and Technology categories, driving significant revenue for Global Superstore.

These insights provide a strategic overview of Global Superstore’s performance across various regions, products, and customer segments to guide future business decisions.

## Data Visualisation and Interpretation
Question 1:

a) What are the three countries that generated the highest total profit for Global Superstore in 2014?

![Top three countries with highest total profit](https://github.com/user-attachments/assets/be8a8f6c-58b0-4449-b59d-c3e3cc0b15e0)

The top three countries by total profit in 2014 are:
United States: 286.40K
China: 150.68K
India: 129.07K

These three countries represent the highest-grossing markets for Global Superstore in 2014. The United States leads with a substantial margin, indicating a mature and profitable market. China and India, being large and rapidly growing economies, also contribute significantly to the company’s bottom line, though at lower levels compared to the U.S.

(b) For each of the top three countries, find the three products with the highest total profit. What are the products’ names and the total profit for each product?

![Profit by Product Name](https://github.com/user-attachments/assets/efc82dcf-d597-421a-91c3-c61fc3f9e4a7)

The Canon ImageCLASS 2200 Advanced Copier is the most profitable product in the United States, contributing significantly to the overall profit with 25.2K, which represents 42.38% of the total profit among the top three products. Cisco Smart Phone, Full Size and Motorola Smart Phone, Full Size also perform well, each contributing around 28% of the total profit. These products are essential in driving profitability, highlighting the importance of high-margin technology products in the U.S. market.

Question 2:

a) Identify the 3 subcategories with the highest average shipping cost in the United States.

![3 subcategories with the highest average shipping cost in the United States.](https://github.com/user-attachments/assets/0681fb83-215d-492b-94cb-16ddb0baf331)

Copiers: Average shipping cost of 165. This is likely due to the large size, weight, and special handling requirements associated with shipping copier machines, which can make the logistics more expensive.
Machines: Average shipping cost of 132. Machines follow with an average shipping cost of 132, which could include various types of equipment or machinery that also require special handling.
Tables: Average shipping cost of 70. Tables have an average shipping cost of 70, which, while lower than the other two categories, still represents a significant cost, likely due to their bulky nature.

Question 3:

![2014 Profit Comparison: Nigeria vs. Other African Countries](https://github.com/user-attachments/assets/36a0b3f8-9aa8-47f2-b522-751e3c75d1a7)

(3a) Assess Nigeria’s profitability (i.e., total profit) for 2014. How does it compare to other African countries?

Nigeria: -23.3K (significant loss)
Zimbabwe: -2.2K (loss)
Uganda: -1.1K (loss)
Other African countries, such as Swaziland, Tunisia, and Ethiopia, had very small profits, ranging from 0.1K to 0.7K.

- Nigeria had a significantly negative profit in 2014, with a total loss of -23.3K, far exceeding the losses seen in other African countries like Zimbabwe and Uganda, which also experienced negative profitability but to a much lesser extent.
- The stark contrast in profitability suggests that Nigeria faced unique and severe challenges that impacted its financial performance. These challenges could include high shipping costs, unfavorable market conditions, or excessive discounting that eroded profit margins.
- The negative profitability in Nigeria is a red flag, indicating the need for a thorough analysis and possible restructuring of the company's strategy in this market. This could involve revisiting pricing, logistics, and marketing strategies to turn the performance around.

(3b): What factors might be responsible for Nigeria’s poor performance? Investigate shipping costs and the average discount as potential root causes.

- While specific data on shipping costs and discounts are not provided in this chart, it is reasonable to infer that these factors contributed to Nigeria's poor performance. High shipping costs, particularly in a market with challenging logistics, can significantly reduce profit margins. Additionally, if the company relied heavily on discounts to drive sales, this could have further eroded profitability.
- Other potential factors might include low customer demand, high competition, or economic conditions specific to Nigeria that made it difficult to achieve profitability. Addressing these issues would require a comprehensive strategy that could involve optimizing the supply chain, adjusting pricing strategies, and focusing on high-margin products.

Question 4:

a) Identify the product subcategory that is the least profitable in Southeast Asia.

Tables in Indonesia: -10,680.28

The Tables subcategory in Southeast Asia, particularly in Indonesia, has the worst profitability, indicating that the demand for this product may be low or the costs associated with selling it are too high. This could be due to factors like high shipping costs, low consumer interest, or pricing issues.

b) Is there a specific country in Southeast Asia where Global Superstore should stop offering the identified subcategory?

Indonesia: Tables subcategory recorded the most significant loss.

- Given the significant loss in the Tables subcategory in Indonesia, Global Superstore might consider discontinuing this product in that market. This action could help reduce losses and allow the company to focus on more profitable product lines.

Question 5:

![image](https://github.com/user-attachments/assets/f2b384d7-5e40-42cb-a94c-fa0bcd3f3acf)

a) Which city is the least profitable (in terms of average profit) in the United States? Disregard cities with less than 10 orders.

- Lancaster is the least profitable city in the United States with an average loss of -157. This significant negative profit indicates that, on average, each order from Lancaster resulted in a substantial loss for Global Superstore.
- Burlington and San Antonio also show considerable negative average profits, with losses of -145 and -124 respectively, indicating these cities are also underperforming.

The reasons for these negative profits could be multifaceted, including high operating or shipping costs, aggressive discounting, or a product mix that is not well-aligned with local demand. These losses suggest that Global Superstore might need to reassess its business strategy in these cities, potentially focusing on reducing costs, optimizing the product mix, or revisiting pricing strategies.

b) Why is this city’s average profit so low?

- Lancaster might have higher-than-average operating costs, such as shipping, warehousing, or local marketing expenses, that reduce profitability.
- Heavy discounting or promotions might be used to drive sales volume, but these could be cutting too deeply into profit margins.
- The products sold in Lancaster may not be aligned with customer preferences, leading to lower sales volumes or margins.
- Addressing these issues could involve analyzing the local market more closely to adjust pricing, reduce costs, and tailor the product offerings to better meet local demand.

Question 6:

a) Which product subcategory has the highest average profit in Australia?

![Product Subcategory with Highest Average Profit in Australia](https://github.com/user-attachments/assets/48d0757d-1c87-413c-9ce2-6b1ded7d0f83)

- The subcategory with the lowest average profit in Australia is Tables, with an average profit of -84, indicating a loss. 
- Appliances are the most profitable subcategory in Australia, with an average profit of 133. This suggests that this product category is in high demand and offers significant margins, making it a key area for focus in the Australian market.
- Copiers and Phones also show strong profitability, with average profits of 105 and 98, respectively. These subcategories likely benefit from high demand and the value customers place on reliable technology and office equipment.
- On the other end of the spectrum, Tables are the least profitable, with a significant negative average profit of -84. This suggests that selling tables in Australia is currently not viable, likely due to high costs, low demand, or both. The company might need to reconsider its strategy regarding this product subcategory in Australia, possibly reducing inventory or reevaluating pricing.

Question 7:

a) Who are the most valuable customers and what do they purchase?

![Top Customers and Their Preferred Purchases](https://github.com/user-attachments/assets/57ecf934-5b26-4174-9e33-27c8a58bfce8)

Most valuable customers prefer Furniture, Office Supplies, and Technology categories.

- Furniture appears to be the dominant category among the top customers, contributing the most to total profit. This suggests that high-value customers are more inclined to purchase big-ticket items like furniture, which typically carry higher profit margins.
- Office Supplies and Technology are also important, particularly for customers like Sanjit Chand and Hunter Lopez, who have a more balanced purchasing pattern across categories.
- Customers like Tamara Chand and Raymond Buch stand out as highly valuable, likely due to their consistent purchases in high-margin categories like furniture. Understanding the preferences and purchasing patterns of these top customers can help Global Superstore tailor marketing efforts, offer personalized promotions, and maintain strong relationships to further enhance profitability.

## Recommendation

- 1. Focus on High-Performing Markets and Products:

United States, China, and India are the top three countries contributing the highest profits. The United States, in particular, is a mature and highly profitable market. Products like the Canon ImageCLASS 2200 Advanced Copier, Cisco Smart Phone, and Motorola Smart Phone have proven to be the most profitable in the U.S. It is recommended that Global Superstore continue to invest in these high-margin products and further strengthen its presence in these key markets through targeted marketing campaigns and strategic partnerships.

- 2. Optimize Shipping Costs in the U.S.:

The subcategories with the highest average shipping costs in the U.S. are Copiers, Machines, and Tables. Since shipping costs significantly impact profitability, it is recommended that Global Superstore explore ways to reduce these expenses. This could include negotiating better shipping rates with carriers, optimizing packaging to reduce weight and dimensions, or considering alternative logistics solutions that lower costs without compromising service quality.

- 3. Address the Profitability Issues in Nigeria:

Nigeria's significant loss in 2014 is a major concern. With a loss of -23.3K, Nigeria's performance is far worse than other African countries. It is recommended that Global Superstore conducts a detailed market analysis in Nigeria to identify specific challenges, such as high shipping costs, low demand, or ineffective pricing strategies. The company should consider restructuring its operations in Nigeria, potentially focusing on reducing costs, optimizing the product mix, or reevaluating pricing and discount strategies to improve profitability.

- 4. Discontinue or Revise the Tables Subcategory in Southeast Asia and Australia:

The Tables subcategory is underperforming in both Southeast Asia (particularly Indonesia) and Australia, where it has generated significant losses. It is recommended that Global Superstore either discontinue this product line in these regions or make substantial revisions to its pricing, marketing, and distribution strategies. By focusing on more profitable product lines, the company can improve overall profitability in these markets.

- 5. Reassess Strategy in Least Profitable U.S. Cities:

Cities like Lancaster, Burlington, and San Antonio are generating significant losses. Global Superstore should conduct a deeper analysis of these markets to understand the root causes of the low profitability. Potential strategies could include adjusting pricing, reducing operational costs, or realigning product offerings to better match local demand. A more tailored approach to these cities could help reverse the trend of negative profits.

6. Capitalize on High-Margin Product Categories in Australia:

- In Australia, Appliances, Copiers, and Phones are the most profitable product subcategories. It is recommended that Global Superstore continue to focus on these categories, possibly expanding their range or increasing marketing efforts to boost sales further. On the other hand, the company should consider reducing inventory or discontinuing the Tables subcategory in Australia due to its consistent underperformance.

7. Nurture Relationships with High-Value Customers:

- High-value customers, particularly those purchasing from the Furniture, Office Supplies, and Technology categories, contribute significantly to Global Superstore’s profits. It is recommended that the company implement loyalty programs, personalized promotions, and targeted marketing campaigns to maintain and enhance these relationships. By understanding and catering to the needs of these customers, Global Superstore can further increase their lifetime value and boost overall profitability.
