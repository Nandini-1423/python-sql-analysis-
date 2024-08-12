
# Python + Sql Analysis (Retail_Orders)


### Summary

This initiative showcases a complete data analytics workflow utilizing Python and SQL. It involves retrieving a dataset from Kaggle via the Kaggle API, processing and refining the data with Pandas, storing the processed data in SQL Server, and conducting an analysis by addressing various inquiries. 


### Highlights
📚 The project  details -

how to download a dataset from Kaggle using the Kaggle API and Python.

🧹 It showcases data cleaning techniques in Pandas, including handling null values, renaming columns, and creating new columns.

📥 The project demonstrates loading the cleaned data into SQL Server using SQL Alchemy.

📊 It explores several data analysis tasks using SQL, such as - 

- finding the top revenue-generating products, 
- identifying the highest-selling products in each region, and calculating month-over-month sales growth.

👍 The project  provides a comprehensive understanding of the data analysis process, from data acquisition to data visualization, and is suitable for data engineers, data analysts, or anyone interested in learning data analysis techniques.

# Installation and Import of Required Libraries for the Project
To facilitate the analysis of the retail orders dataset using SQL and Python, the following libraries need to be installed and imported into your Jupyter Notebook environment:

 ## OpenDatasets:-
 This library assists in easily downloading datasets from Kaggle.

      pip install opendatasets  
## Pandas:
 A powerful data manipulation and analysis library essential for handling structured data.

      pip install pandas  
## SQLAlchemy: 
A comprehensive library for database interactions in Python, providing a high-level API for SQL database operations.

      pip install sqlalchemy  

## Operating System Library (os): 
A built-in Python library that offers functionalities for interacting with the operating system, such as file and directory management.

      import os  

## Example Code Snippet
After installing the necessary libraries, you can import them into your notebook as follows:

  ### Importing libraries  
      import os  
      import pandas as pd  
      import sqlalchemy as sal  

With these libraries in place, you are well-equipped to proceed with the data importation and analysis of the retail orders dataset.

--------------------------------------------

 To load a dataset into SQL Server using Pandas, you can follow these steps. Make sure you have the necessary libraries installed and a valid ODBC data source connection string for your SQL Server database. Below is a step-by-step guide and example code snippet to help you achieve this.


 ## Steps to Load Dataset into SQL Server
 ### 1. Set Up the SQLAlchemy Engine: 
  Establish a connection to the SQL Server    database using SQLAlchemy.

###  2. Load Your Dataset: 
You can read the dataset into a Pandas DataFrame.

### Upload the DataFrame to SQL Server:
 Use the to_sql()
 method of the DataFrame to load the data into your specified SQL Server table.

## Example Code Snippet
### Here’s how you can put this all together:



     import pandas as pd  
     import sqlalchemy as sal  

     # Step 1: Create SQLAlchemy Engine  
     engine = sal.create_engine('mssql+pyodbc://username:password@your_server/your_database?  driver=ODBC+Driver+17+for+SQL+Server')  

     # Step 2: Load your dataset into a DataFrame  
     # Replace 'your_dataset.csv' with your actual dataset file  
     data = pd.read_csv('your_dataset.csv')  

     # Step 3: Upload DataFrame to SQL Server  
     # Replace 'your_table_name' with the name of your SQL table  
     data.to_sql('your_table_name', con=engine,  if_exists='replace', index=False)  

     print("Dataset loaded successfully into SQL Server.")

## Notes:
 
To load a dataset into SQL Server using Pandas, you can follow these steps. Make sure you have the necessary libraries installed and a valid ODBC data source connection string for your SQL Server database. Below is a step-by-step guide and example code snippet to help you achieve this.

### Steps to Load Dataset into SQL Server

1. **Set Up the SQLAlchemy Engine**: Establish a connection to the SQL Server database using SQLAlchemy.

2. **Load Your Dataset**: You can read the dataset into a Pandas DataFrame.

3. **Upload the DataFrame to SQL Server**: Use the  `to_sql()` method of the DataFrame to load the data into your specified SQL Server table.

### Example Code Snippet

Here’s how you can put this all together:

```python
import pandas as pd
import sqlalchemy as sal

# Step 1: Create SQLAlchemy Engine
engine = sal.create_engine('mssql+pyodbc://username:password@your_server/your_database?driver=ODBC+Driver+17+for+SQL+Server')

# Step 2: Load your dataset into a DataFrame
# Replace 'your_dataset.csv' with your actual dataset file
data = pd.read_csv('your_dataset.csv')

# Step 3: Upload DataFrame to SQL Server
# Replace 'your_table_name' with the name of your SQL table
data.to_sql('your_table_name', con=engine, if_exists='replace', index=False)

print("Dataset loaded successfully into SQL Server.")
```

### Notes:
- **Connection String**: Modify the connection string (`'mssql+pyodbc://username:password@your_server/your_database?driver=ODBC+Driver+17+for+SQL+Server'`) with your actual SQL Server credentials and the appropriate ODBC driver.
- **Table Management**: The argument `if_exists='replace'` will replace the existing table, if it exists. You can change it to `'append'` to add data to an existing table without dropping it.
- **Index Handling**: The parameter `index=False` ensures that the DataFrame index is not written to the SQL table.

With these steps, your dataset should be successfully loaded into SQL Server and ready for analysis!

After connecting to SQL Server from your Jupyter Notebook and loading your dataset into a pandas DataFrame, you can execute SQL queries to analyze the data directly. To find the top ten highest revenue-generating products, follow these steps:

## Steps to Query SQL Server

### 1. Make sure you're connected to the SQL     Server:   
  Ensure that your SQLAlchemy engine is set up as mentioned in the previous response.
### 2. Execute the SQL Query: 
You can use **pd.read_sql_query()** to execute SQL queries directly against your database and return the results as a DataFrame.

### Example Code Snippet

 Assuming you have a table named orders that contains the product information and revenue, your query might look like this:
    
        import pandas as pd  
        import sqlalchemy as sal  

        # Create SQLAlchemy Engine (modify with your actual connection string)  
        engine = sal.create_engine('mssql+pyodbc://username:password@your_server/your_database?driver=ODBC+Driver+17+for+SQL+Server')  

        # SQL query to find the top ten highest revenue-generating products  
        query = """  
        SELECT product_name, SUM(revenue) AS total_revenue  
        FROM orders  
        GROUP BY product_name  
        ORDER BY total_revenue DESC  
        LIMIT 10;  
        """  

       # Execute the query and load the results into a DataFrame  
       top_ten_products = pd.read_sql_query(query, engine)  

       # Display the results  
       print(top_ten_products)


### Queries to be perform :

     1. Find top ten highest devenue generating products.
     2. 2. Find top five highest selling products in each region. 
     3. find month over month growth comparison for 2022 and 2023.
     4. order by year (order_date) , month (order_date)
     5. For each category which month had highest sales.
     6. Order by category, format (order_ date,'YYYYMM')
     7. Which sub_category had highest growth by profit in 2023 compared to 2022.
     8. Order by year (order_date), month (order_date)


## Notes:
 - Make sure to adjust the table name (sales), and the column names (revenue, order_date, category, sub_category, profit) per your actual database schema.
 - The SQL syntax might slightly vary based on the SQL Server version you are using. The examples provided assume compatibility with SQL Server syntax.
 - You can execute these queries in the same manner as shown in the previous responses, using pd.read_sql_query().



 💻  😄 🚀  ⚙️ 🐍 ✏️
 


