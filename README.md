# powerbi_star_datamodel
Turned a dataset of 23 tables with raw data, inconsistent naming, duplicates, chaotic relationships into a star schema with fact and dimension tables; shared date dimension table; configured security roles; ready for analysis and trustworthy reporting.

### :heavy_exclamation_mark: Raw data in Power BI (Before)

<img width="1604" height="1008" alt="image" src="https://github.com/user-attachments/assets/9677fc34-3778-4698-abaf-b7c7ee909384" />

### :heavy_check_mark: Star Schema in Power BI (After)

<img width="1913" height="962" alt="image" src="https://github.com/user-attachments/assets/7e22793c-5887-40cd-aac1-a6294c48b57a" />

## :bar_chart: Business Goal
Organize raw data into a structured data model for simple business reporting with correct numbers.

Make slicing, dicing, filtering, and aggregating data (like tracking monthly sales by region or product category) much more intuitive for analysts and non-technical users.

## :pencil2: Specifications
1) Data source: Excel file

Open Power BI Desktop, click Get Data, choose your source, and click Transform Data to launch the Power Query Editor.

2) Data capitalization standards: 
- Language => English
- Capitalization => snake_case
- Tables => starting from fact_  dim_
- Keys => _key (new-added) or _id (from the source file)
- Naming => Human Readable

## :white_check_mark: Implementation Steps in Power Query and Power BI

 ### :bookmark_tabs: Data exploration
- Check all available tables
- Understand the business
- Understand the data
- Spot dimension and fact tables
- Baseline key numbers

### :crown: Data preprocessing 
- Replacing NULL values with custom values. In the Power Query Editor, go to the Transform tab. Click on Replace Values.
- Divide data per columns. Use Unpivot, Splitting Columns by delimeter, Getting Rows functionality. Trim data after dividing.
- Append queries to combine multiple tables into a single table (for example, Orders_2025 and Orders_2026)
- Map the data, using Merge by column
- Capitalize Each Word (for example, Customer Name)
- Format the data types (for example, same DateTime format, same numerical format for the whole dataset)
- Remove duplicates. Use Group By and Count to identify duplicated rows, then delete not valuable rows

### :star: Data modeling - STAR schema
- Build Dimension table as a reference query
- Create a dedicated Date table to handle time intelligence
- Build Fact Table as a reference query
- Enable load for source tables to avoid duplicated tables in the data model
- Load the clean tables into Power BI
- Establish One-to-Many relationships with single direction filtering in Power BI Model View
- Apply security rules (for example, each user can access the sales data for their assigned region)

## :open_file_folder: Result file

Download the powerbi_stars_datamodel.pbix file. Open it in Power BI Desktop. Go to Model view to analyze the schema. 

## Example of data modeling process
Source Sales table contains ProductName column
<img width="1918" height="1027" alt="image" src="https://github.com/user-attachments/assets/f6cab14a-b3fe-4326-b87f-b12f26956059" />
Merging it with Product dimension table dim_product
<img width="1918" height="1031" alt="image" src="https://github.com/user-attachments/assets/fc7888cd-6c18-41e1-98fc-53836c0b8d10" />
Adding column with product_key to fact_sales table, creating a clear relationship between dim and fact tables
<img width="1917" height="1028" alt="image" src="https://github.com/user-attachments/assets/fc98f55f-d28c-40be-8904-1e84bcd71d56" />

