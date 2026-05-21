# Power Query Data Transformation Project

## 1. Project Overview
This project is about cleaning and combining data using Power Query in Power BI. The main data comes from a local folder containing monthly sales sheets. The goal was to clean the data, fix errors, and make it ready for future reporting.

---

## 2. Data Sources Used
* **Sales Data Folder:** Loaded directly from the folder path: `F:\RW\power BI\Projects\Sales Data` using the `Folder.Files` connector. It has monthly sales files (January, February, March, and April).
* **Employee Data:** A separate file containing employee details like EmployeeID and their operational regions.

---

## 3. Power Query Applied Steps
My actual data transformation follows these standard steps in the Power Query editor:
1. **Source:** Connected to the main local folder path to see all available files.
2. **Filtered Hidden Files:** Removed any temporary or hidden system files from the list.
3. **Invoke Custom Function1:** Power Query automatically ran a custom function to open, combine, and merge all monthly sales files into one single table.
4. **Rounded Off:** Adjusted the numbers, changed columns to correct data types (like Date and Currency), and rounded the final sales values.

---

## 4. Other Transformations Made
* **Data Profiling:** Turned on `Column Quality` and `Column Distribution` from the View tab to find missing values (nulls) and errors in the columns.
* **Unpivot Columns:** Changed wide horizontal tables into vertical rows using `Unpivot Other Columns` to get proper `Month` and `Monthly_Sales` columns.
* **Grouping:** Grouped the data by `Region` to calculate `Total Sales`, `Average Order Value`, and `Transaction Count` in a summary table.

---

## 5. Main Problems Faced & How I Solved Them

### Problem 1: Many-to-Many Relationship Risk (Merging Issue)
* **The Problem:** Sir asked to combine Sales Data with Employee Data. But Sales Data only has `Region` and Employee Data has `EmployeeID`. If I merge them directly using Region, it makes a **Many-to-Many** connection. This duplicates rows and makes the total sales amount wrong.
* **My Solution:** To keep the sales data safe and accurate, I did not merge them inside Power Query. Instead, I made a `Reference` copy table named `Q1_Sales_Data` and decided to handle the relationship later in the Power BI Model View.

### Problem 2: Data Turned into Binary and Disappeared
* **The Problem:** While changing the parameters and source settings, Power Query cached the source folder and suddenly the clean data disappeared. It only showed raw Binary files, and the rows were hidden.
* **My Solution:** I did not panic or delete my steps. I went to the **Applied Steps** panel on the right side and clicked on my very last step called **`Rounded Off`**. This refreshed the query cache and immediately brought back all my cleaned data and historical steps perfectly.

---

## 6. Automation Testing (Refresh Simulation)
To check if the project is automated:
1. I added a new file named `Sales_Apr.xlsx` into the source folder.
2. I clicked the **`Refresh Preview`** button in Power Query.
3. The system automatically found the new file, combined it, and applied all my cleaning steps down to the `Rounded Off` state without any manual work.
