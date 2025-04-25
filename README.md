# Prediction-of-Airbnb-Rental-Prices-using-Machine-Learning  
**Data Stewardship Part 2**

---

## Repository overview  
This GitHub repo contains only the files necessary for modeling. Large raw and intermediate CSVs are not checked in for storage space reasons and must be downloaded via OneDrive/SharePoint.

### Folder structure 
├── data/
│   ├── raw/                 # placeholder for AB_US_2023.csv
│   ├── mid_processing/      # placeholder for AB_US_2023_DATA_CLEANED.csv
│   ├── processed_data/      # placeholder for AB_US_2023_PROCESSED.csv
│   └── sampled_data/        # stratified subsamples (train/test), versioned in DBRepo
├── data/zcta/               # ZCTA shapefiles for ZIP-code encoding
├── results/                 # final artifacts: models, plots, test_metrics.csv
├── report/                  # detailed PDF report
│   └── Prediction of Airbnb Rental Prices using Machine Learning.pdf
├── Data_Exploration.ipynb
├── Pre_processing.ipynb
├── ZIP-Code encoding.ipynb
├── Modeling_Regression.ipynb
└── README.md
---



## Downloading Large Data Files  
1. **Raw and Intermediate CSVs**  
   - **Link (OneDrive/SharePoint):**  
     `https://tuwienacat-my.sharepoint.com/:f:/g/personal/e12327971_student_tuwien_ac_at/Ei4OQwdYYXJBvkgyrpgQOkMBmbvwrhTqC6YCQP6Q8UtzQQ?e=7Hd7tC`  
   - Targets:  
     - `data/raw/AB_US_2023.csv`  
     - `data/mid_processing/AB_US_2023_DATA_CLEANED.csv`  
     - `data/processed_data/AB_US_2023_PROCESSED.csv`  

2. **ZCTA Shapefile**  
   - **Link:**  
     `https://tuwienacat-my.sharepoint.com/:u:/g/personal/e12327501_student_tuwien_ac_at/EdmpPAIWJdlBhMZFuD4YQUkBdLmbF7EOSdesEdLkq7z3bA?e=5iD0J0`  
   - Place contents into `data/zcta/`

---

## Versioned Subsamples in DBRepo  
Because DBRepo does not support splits in its GUI, the stratified training and test subsamples were generated locally in `data/sampled_data/` and then uploaded to **DBRepo**. In **Modeling_Regression.ipynb**, they are retrieved via the API:

- **Train-Split PID:**  
  `https://test.dbrepo.tuwien.ac.at/.../subset/6a811a49-2142-11f0-8d13-0e8cdc00dc05/info`  
- **Test-Split PID:**  
  `https://test.dbrepo.tuwien.ac.at/.../subset/3b1a9519-2142-11f0-8d13-0e8cdc00dc05/info`

---

## Running the Notebooks  

### Type 1: Standalone Regression Analysis  
1. Clone the GitHub repository and configure your DBRepo API credentials.  
2. In **Modeling_Regression.ipynb**, execute the cells that start with `%pip install`.  
3. Run the notebook — the results will be saved in the `results/` folder.

### Type 2: Full Workflow Replication  
1. Download the large CSVs and ZCTA shapefile and place them under `data/`.  
2. In each notebook, run the `%pip install` cells.  
3. Execute **Data_Exploration.ipynb** (optional).  
4. Execute **Pre_processing.ipynb** to generate `AB_US_2023_DATA_CLEANED.csv`.  
5. Execute **ZIP-Code encoding.ipynb** to update `AB_US_2023_PROCESSED.csv`.  
6. In **Modeling_Regression.ipynb**, verify the filepath to `data/processed_data/AB_US_2023_PROCESSED.csv`.  
7. Run **Modeling_Regression.ipynb** — the models, plots, and `test_metrics.csv` will appear in `results/`.

---

## Results and Artifacts  
The `results/` folder will automatically contain:  
- **Models + Scalers:** `.pkl` files  
- **Performance Metrics:** `test_metrics.csv`  
- **Plots:** residuals, histograms, and true-vs-predicted visualizations as `.png`

These files can then be manually uploaded to TUWRD to obtain a DOI for the results archive.

---

## Environment & Dependencies  
- Python ≥ 3.8  
- Install requirements by running the %pip install cells in each notebook.
- Git is needed to clone and version-control the repository.