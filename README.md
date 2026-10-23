#  Nashville Housing Data Cleaning in SQL

##  Project Overview
This project focuses on cleaning and standardizing a real estate dataset (Nashville Housing Data) using SQL. Real-world data is often messy, inconsistent, and contains missing values. The objective of this project is to transform raw data into a clean, structured format ready for exploratory data analysis (EDA) and visualization.

## 🛠️ Tools Used
- **SQL** (SQL Server / MySQL)
- **Dataset:** [Nashville Housing Data](https://www.kaggle.com/datasets/teminice/nashville-housing-data)

## 🧹 Data Cleaning Steps Performed

### 1. Standardizing Date Format
- Converted the `SaleDate` column into a standard `DATE` format.
- Created a new column `SaleDateConverted` and updated the table to ensure consistency.

### 2. Populating Missing Property Addresses
- Identified rows with null `PropertyAddress`.
- Used a **Self-Join** on `ParcelID` to populate missing addresses using data from other records with the same Parcel ID.

### 3. Splitting Address into Individual Columns
- Split the `PropertyAddress` into two separate columns: `PropertySplitAddress` and `PropertySplitCity` using `SUBSTRING` and `CHARINDEX`.
- Split the `OwnerAddress` into three separate columns: `OwnerSplitAddress`, `OwnerSplitCity`, and `OwnerSplitState` using the `PARSENAME` function.

### 4. Standardizing Categorical Data
- Changed inconsistent values in the `SoldAsVacant` field from 'Y' and 'N' to 'Yes' and 'No' using `CASE` statements for better readability.

### 5. Removing Duplicate Records
- Used a **Common Table Expression (CTE)** with the `ROW_NUMBER()` window function to identify duplicate rows based on `ParcelID`, `PropertyAddress`, `SalePrice`, `SaleDate`, and `LegalReference`.
- Deleted duplicate records to ensure data integrity.

### 6. Deleting Unused Columns
- Dropped original, unused columns (`OwnerAddress`, `TaxDistrict`, `PropertyAddress`, `SaleDate`) to keep the final dataset clean and optimized.

##  How to Run
1. Import the `NashvilleHousing.csv` dataset into your SQL database.
2. Open the `Data Cleaning Portfolio Project Queries.sql` file.
3. Execute the queries sequentially to clean the data.

##  Outcome
The final cleaned dataset is now fully standardized, free of duplicates, and properly structured, making it ready for advanced analysis and dashboard creation in tools like Power BI or Tableau.
