# NotebookCodeStyle_ForConf
This is the code for analyzing Jupyter Notebook Code Style Issues. To reproduce the results, you need to clone this project or download the entire project, including the data directory. Then, run the following notebook files to get the results. The notebook file entitled `2023_Conf_NB_Code_Style_Analysis.ipynb` contains the code for result analysis. The other three are for data pre-processing and storing in the database.       

## Notebook Files
**`2023_Conf_NB_Code_Style_Analysis.ipynb`** - To replicate the results reported in this paper, execute 2023_Conf_NB_Code_Style_Analysis.ipynb. It is a notebook file where the markdown cells describe the code sections sequentially. 

**`2023_Conf_NB_Pylint_Execution.ipynb`** - This notebook contains the code for Pylint execution. It works on notebook files and generates text files containing code style issues and quality ratings.   

**`2023_Conf_NB_Pylint_Sqlite_DB.ipynb`** - This notebook contains database handling code, having all the functions, i.e., connect, create, insert, etc. This notebook has the code to process the Pylint output and insert the information into the database table. 

**`2023_Conf_Pylint_NB_Text_Analysis.ipynb`** - This notebook contains the code for renaming the output ipynb file name. 

## Data
We stored the data in a SQLite database. The db file is available in data/ directory. The database consists of the following tables:
```
+-------------------+
|      database     |
+-------------------+
| NBFILES           |
| NBRATING         |
| NBISSUE          |
| ISSUEFREWQUENCY   |
+-------------------+
```
1. **`NBFILES`** — a table that stores the notebook Filename, and its Type (notebook type: ml or non-ml).
```
+-------------------+	
|      NBFILES     |	
+-------------------+	
| Filename          |	
| Type              |	
+-------------------+	
```
2. **`NBRATING`**  — a table that stores the notebook Filename and its Rating (INT value ranges 0 to 10).

```
+-------------------+	
|      NBRATING     |	
+-------------------+	
| Filename          |	
| Rating            |	
+-------------------+	
```

3. **`NBISSUE`**  — a table that stores the the notebook Filename, Issue (Pylint issue code), Cell Number (the code cell containing the issue), and Line (line number containing the issue).

```
+-------------------+	
|      NBISSUE      |	
+-------------------+	
| Filename          |	
| Issue             |	
| CellNo            |	
| Line              |	
+-------------------+	
```
4. **`ISSUEFREWQUENCY`**  — a table that stores the the notebook Filename, Issue Code (Pylint issue code), Frequency (number of occurance of the recpective issue in the notebook), and Type (noteboook type: ml or non-ml).

```
+-------------------+	
|  ISSUEFREWQUENCY  |	
+-------------------+	
| Filename          |	
| Type              |	
| Code              |	
| Frequency         |	
+-------------------+	
```
Notebooks used in this empirical study can be available at https://zenodo.org/records/4468523 

The result of this study has been published at the IEEE 23rd International Working Conference on Source Code Analysis and Manipulation (SCAM). 

M. S. Siddik and C. -P. Bezemer, "Do Code Quality and Style Issues Differ Across (Non-)Machine Learning Notebooks? Yes!," 2023 _IEEE 23rd International Working Conference on Source Code Analysis and Manipulation (SCAM)_, Bogotá, Colombia, 2023, pp. 72-83, doi: 10.1109/SCAM59687.2023.00018.
