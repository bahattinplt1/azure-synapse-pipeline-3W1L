# Azure Synapse Product Data Pipeline

This project demonstrates a data ingestion pipeline using **Azure Synapse Analytics** to load and transform product data from a CSV file into a dedicated SQL pool.

## 📂 Files Included

- `Product.csv`: The source file containing raw product data.
- `sqlscript.csv`: Exported data from the target `dbo.DimProduct` table after running the pipeline.
- `LoadProductData.json`: Pipeline definition file, designed in Synapse Studio to trigger the data flow and handle staging.
- `screenshots/`: Step-by-step visuals of the entire process including setup, configuration, and execution.

> **Note:** This pipeline references a data flow named `LoadProductsData`, which is not included in this repository. The data flow can be recreated manually by following the documented steps or added in a future update.

## 🧩 What the Pipeline Does

1. Reads product data from `Product.csv` stored in Azure Data Lake (Gen2).
2. Triggers a data flow (not included here) to:
   - Check whether each product already exists in the `dbo.DimProduct` table.
   - Insert new records or update existing ones based on a match on `ProductAltKey`.
3. Loads the processed data into the dedicated SQL pool table.

## 🚀 How to Use

1. Upload `Product.csv` to your Synapse-linked Data Lake under `files/data/`.
2. Import `LoadProductData.json` in Synapse Studio (via Integrate > Pipeline).
3. Recreate the missing data flow (`LoadProductsData`) by following documented transformations:
   - Source from CSV
   - Lookup against SQL table
   - Alter row with insert/upsert logic
   - Sink to `dbo.DimProduct`
4. Run the pipeline manually or configure a trigger.
5. Query the table to verify the results.

## 🖼 Screenshots

Screenshots included in the `screenshots/` folder provide a visual reference for:
- Creating the Synapse pipeline
- Defining source/destination
- Data preview and debug steps
- Final result validation

---

Built as a hands-on learning project to understand data transformation pipelines on Azure Synapse.  
Feel free to fork, recreate the data flow, or enhance the pipeline for your own use cases!
