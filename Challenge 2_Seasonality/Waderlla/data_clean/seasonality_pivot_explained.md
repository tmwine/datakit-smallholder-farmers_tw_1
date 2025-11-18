## Creating the Pivot Table for Seasonality Analysis (Challenge 2)

The pivot table was created from the cleaned dataset `proc_challenge_2_seasonality`, stored in the data model. The objective was to calculate how frequently farmers’ questions occur across time (year, quarter, month), country, language, and thematic categories.

---

### 1. Input Data

- **Source:** the table `proc_challenge_2_seasonality` loaded into the workbook’s Data Model (Power Query → Data Model).
- **Available source columns:**
  - `question_id`
  - `question_language`
  - `question_topic`
  - `question_sent` (timestamp of the question)
  - `question_user_country_code`
  - `topic_category`
  - `topic_type`

Data for the year **2017** was excluded during preparation because it did not contain a full set of observations.

---

### 2. Creating the Pivot Table

1. **Creating a pivot from the Data Model:**
   - In Excel, the command **Insert → PivotTable** was used.
   - The data source was set to:  
     **“Use this workbook’s Data Model.”**
   - The table `proc_challenge_2_seasonality` was selected as the field source.

2. **Automatic date grouping:**
   - After dragging the `question_sent` field into the **Rows** area, Excel automatically generated the following grouped levels:
     - **Year**
     - **Quarter**
     - **Month**
   - These fields did not exist in the original source table — they were created dynamically by the PivotTable engine.

---

### 3. Pivot Table Field Configuration

The fields were arranged in the **PivotTable Fields** panel as follows:

#### **Rows:**

- `question_user_country_code`
- `question_language`
- `question_sent (Year)`
- `question_sent (Quarter)`
- `question_sent (Month)`
- `topic_category`
- `question_topic`
- `topic_type`

Each row in the pivot table represents a unique combination of:

**country × language × year × quarter × month × topic category × question topic × topic type.**

This structure allows seasonal analysis not only at a high level (e.g., *cereals*) but also for detailed topics (`question_topic`) and types of inquiries (`topic_type`, such as `planting_growing`, `pests_disease`, `weather`).

#### **Columns:**
- No fields were placed in the Columns area.

#### **Values:**
- `Count of question_id`  
  The aggregation measure counting the number of questions for each combination of row fields.

#### **Filters:**
- No global filters were applied in this pivot configuration.

---

### 4. Purpose and Usage of the Pivot

The resulting pivot table serves as an intermediate dataset for building visualizations in **Tableau** as part of Challenge 2 (Seasonality).

It enables:

- analysis of seasonal patterns in farmers’ questions (e.g., whether *cereals* or *livestock* topics peak in Qtr1/Qtr4),
- comparison of trends across countries and languages,
- examination of which detailed topics (`question_topic`) and inquiry types (`topic_type`) appear most frequently in each time period.

---

### 5. Renaming Fields for Tableau

To improve clarity and consistency in Tableau, the following name adjustments were applied:

- `question_user_country_code` → **Country Code**  
- `question_language` → **Language**  
- `question_sent (Year)` → **Year**  
- `question_sent (Quarter)` → **Quarter**  
- `question_sent (Month)` → **Month**  
- `topic_category` → **Topic Category**  
- `question_topic` → **Question Topic**  
- `topic_type` → **Topic Type**  
- `Count of question_id` → **Number of Questions**

---

### 6. Saving the Final Pivot

The completed pivot table was exported and saved as:

**`Final_Pivot_Data.xlsx`**

This file serves as the final input dataset for downstream Tableau dashboards and analyses.

---
