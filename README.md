# Microsoft-Fabric
![Screenshot 2024-06-09 110925](https://github.com/AlfredDamilare/Microsoft-Fabric/assets/138758961/1561954a-8afe-49ae-9f3a-69013bc7cd76)
![Screenshot 2024-06-09 110939](https://github.com/AlfredDamilare/Microsoft-Fabric/assets/138758961/c777f740-c713-460b-9341-e6df9c109b9d)
![Screenshot 2024-06-09 110932](https://github.com/AlfredDamilare/Microsoft-Fabric/assets/138758961/4fdb6d06-2c29-4087-8101-f99138260102)
### Explanation of Findings in Microsoft Fabric Notebook

Based on the extracted content from your Jupyter notebook, it appears that you have performed various data analysis and visualization tasks. Here is a brief summary and explanation of your findings:

#### 1. Data Preparation
- **SQL Queries:** You extracted and prepared sales data using SQL queries, selecting relevant columns like `OrderYear` and `GrossRevenue`.
    ```sql
    SELECT YEAR(OrderDate) AS OrderYear,
           SUM((UnitPrice * Quantity) + Tax) AS GrossRevenue
    FROM salesorders
    GROUP BY YEAR(OrderDate)
    ORDER BY OrderYear;
    ```

- **Data Loading:** You loaded the data into a DataFrame for further analysis.
    ```python
    df = spark.sql("SELECT * FROM APH.salesorders LIMIT 1000")
    display(df)
    ```

#### 2. Data Analysis
- **Revenue Analysis:** You created visualizations to analyze revenue trends.
  - **Line Chart:** Displayed gross revenue over different years.
    ```python
    import seaborn as sns
    ax = sns.lineplot(x="OrderYear", y="GrossRevenue", data=df_sales)
    plt.show()
    ```

  - **Bar Chart and Pie Chart:** Visualized revenue by year and the distribution of orders per year.
    ```python
    from matplotlib import pyplot as plt
    fig, ax = plt.subplots(1, 2, figsize = (10,4))
    ax[0].bar(x=df_sales['OrderYear'], height=df_sales['GrossRevenue'], color='orange')
    yearly_counts = df_sales['OrderYear'].value_counts()
    ax[1].pie(yearly_counts)
    ax[1].legend(yearly_counts.keys().tolist())
    fig.suptitle('Sales Data')
    plt.show()
    ```

#### 3. Key Findings

- **Trend Analysis:** The Sum of COGS showed a significant increase, particularly between September 2013 and December 2014, with a notable rise of 168.06%.
- **Mid-2014 Spike:** There was a rapid increase in COGS starting from July 2014, with a 38.92% rise over five months.
- **Steepest Increase:** The most dramatic rise in COGS occurred between July 2014 and December 2014, from $7,179,054.5 to $9,973,022.

#### 4. Insights

- **Significant Growth:** The data indicates a substantial growth in costs over the analyzed period, particularly in the latter half of 2014.
- **Focus Areas:** The USA had a major contribution to overall COGS, suggesting the need for deeper analysis of cost drivers within this region.
- **Actionable Steps:** Develop strategies for cost management, especially during periods of rapid increase.

### Conclusion

Using Microsoft Fabric, you have effectively prepared and analyzed sales data to uncover significant trends and insights. The findings highlight critical periods of cost escalation, especially in the USA, and provide a basis for strategic decision-making and cost management.
Link To Project https://app.powerbi.com/links/0dB4iLSTwr?ctid=2ce0dcca-5db8-4c38-81e4-a57c0bee694c&pbi_source=linkShare&experience=power-bi
