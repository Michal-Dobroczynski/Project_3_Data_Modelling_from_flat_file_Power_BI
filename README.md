# Building data model in Power BI from flat file (.csv file)

### How to convert flat file to Beautiful data models? - Best Practices

**What are flat files?** </br>

It's typical file which we receive and have to clean/transform for data analysis. For examples files in .csv format.

![flat_file](https://user-images.githubusercontent.com/127090462/224746179-23cfc335-db86-4152-acda-8f5372c2a27b.JPG)

Source of file: https://www.kaggle.com/datasets/kyanyoga/sample-sales-data

### Key steps to build a good data model in Power BI?

1) **Building star schema model (fact table vs dimension tables)**
2) **Creating relationships between tables**
3) **Creating date table (calendar table) for our data model**
4) **Preparing Key Measures for calculations**

Let's go through all the points

**1) Building star schema model (fact table vs dimension tables)**

In Power BI we need to divide this flat file into logical groups for building data models.

In our data model we will use star schema, what is it?

Star schema is the simplest style of data mart schema and is the approach most widely used to develop data warehouses and dimensional data marts. The star schema consists of one or more fact tables referencing any number of dimension tables:

- Fact table (data which we are able to calculate like sales, quantity, amount)
- Dimension tables (data for which we want to filter our fact table, like customers, regions,  order type)

![star_schema](https://user-images.githubusercontent.com/127090462/224748482-9c843567-5379-49df-b9bc-13bd5f8e9766.JPG)

source: https://learn.microsoft.com/en-us/power-bi/guidance/star-schema

From our flat file we can create separate tables for customers, products which will be our dimensions tables.
Sales information will be put in our fact tables 

Why do we do that conversion from flat file to data model like star schema?
- **Readability** - easier to work with 
- **Optimization** - improved performance. In business, large fact tables have millions of rows
- **Convenience** - adding new data, new filter is much easier in form of data model than adding this data to flat file
- **Cardinality/Redundancy** - we reduce cardinality of different tables. Cardinality is like the number of unique columns within table which improve performance

## Which steps do we have to take to build a data model in Power BI?

- import flat file to Power Query editor in Power BI -> transform data

# ZDJĘCIE WRZUĆ

- create 2 separate dimension tables (Customers and Products) and our fact table Orders.

From our flat file which will be our fact table - orders, I moved all data to those 2 created tables which refer to Customers and Products data (dimension tables). 
In these dimension tables I removed duplicates and added an Index column which will help us make a relationship between the fact table and dimension tables. 
- Product_ID
- Customer_ID

# ZDJĘCIE WRZUĆ

2) **Creating relationships between tables**

**What are relationships?**

A table relationship works by matching data in key fields — often a field with the same name in both tables. In most cases, these matching fields are the primary key from one table, which provides a unique identifier for each record, and a foreign key in the other table.

Here is our data model with automatic relationship created by Power BI:

Type of relationships in our data model is one-to-many

![relationship](https://user-images.githubusercontent.com/127090462/224754608-7be7901a-90c9-45c4-b234-f3fbefa6d8ec.JPG)


**What are types of relationships between tables?**
- One-to-many (1:*) 
- Many-to-one (*:1) 
- One-to-one (1:1) 
- Many-to-many (*:*)

 (source: https://learn.microsoft.com/en-us/power-bi/transform-model/desktop-relationships-understand)

The one-to-many and many-to-one cardinality options are essentially the same, and they're also the most common cardinality types.

3) **Creating date table (calendar table) for our data model**

- Next very important step and it's good practice in building a data model is creating a date table (calendar table)

Using Power BI Calendar function we will be able to create date table and  filter our report by attributes like Year, Month, and any other aggregation of time is required. 

Data table in our model:

# ZDJĘCIE WRZUĆ

- Now we have to remember to make a connection/relationship between our new date table with our fact table (orders).

![relationship_2_date_table](https://user-images.githubusercontent.com/127090462/224757268-88bcd95b-999c-4935-96cb-3ad632b40056.JPG)

4) **Preparing Key Measures for calculations**

- Last, but not least step is to create Key Measures which we will be using in Power BI for calculations

![Key_Measures](https://user-images.githubusercontent.com/127090462/224757677-635abddd-89c9-4612-b8ad-2eb037d218fc.JPG)

