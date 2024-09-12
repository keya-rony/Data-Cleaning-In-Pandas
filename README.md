# Data-Cleaning-In-Pandas
Data Cleaning In Pandas Project


## Project Overview
This analysis focuses on creating a targeted call list for the sales team to support an upcoming marketing campaign. The initial dataset was unstructured and required significant cleaning and refinement to produce an efficient and streamlined list of customers to contact.

I was motivated to carry out this project to showcase my data cleaning skills using pandas. Through this project, I aimed to transform messy, raw data into a valuable asset that could directly contribute to a more focused and data-driven sales strategy.


<!--![Alt text](CallList.png)-->

<p align="center">
  <img src="CallList.png" alt="Alt text" width="400" height="200"/>
</p>

### Data Source and Tools Used
The dataset used in this project is a fictional one provided by Alex the Analyst, a YouTube content creator known for his data analysis tutorials. For the entirety of this project, I relied on pandas to handle the data cleaning process.

The dataset presented several common issues, including missing values, unwanted characters in the customer name column, inconsistent data formatting across multiple columns, and phone numbers stored in the wrong format. These issues made the data unsuitable for analysis, requiring extensive cleaning before it could be used effectively to generate a targeted call list.

### Data Cleaning
The following are the data cleaning steps taken from start to end to obatined the required call list.
1. Loading the data
2. Checking for duplicates and removing duplicates
3. Removing unwanted columns
4. Fixing Datatypes
5. Handling Missing values

#### Loading the Data
```python
import pandas as pd

df = pd.read_csv('Customer Call List.xlsx')
df.head()
```
After loading the data I carried out some data exploration to understanding the data contents
```python
df.info()
```

```python
df.shape
```
#### Checking for duplicates and Removing duplicates
```python
df.duplicated().sum()
```
The data returned one duplicate value, which I proceeded to drop
```python
df = df.drop_duplicates()
```
#### Removing the unnecessary column(s)
Considering what the report is going to be used for, I removed columns that are not necessary. The only columns necessary are CustomerID, FirstName,LastName,Phone_Number,Address, PayingCustomer and DoNotContact
```python
df = df.drop(columns = "Not_Useful_Column")
df
```
#### Fixing the Last_Name Column
The Last_Name column contained unwanted characters like _, / and ... on the left and right. I applied the strip("123") method to remove any leading or trailing characters in the string that match the ones inside the quotes. In this case, to strip any leading or trailing 1, 2, 3, ., _, or / from the values in the 'Last_Name' column..

```python
df = df['Last_Name'].str.strip("123._/")
df
```
#### Fixing the Phone Number Column
The phone number column contains unwanted characters such as / and | as shown below

![Alt text](./images/your-image.png)

