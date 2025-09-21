<h1 align="center"> ECE2112 Programming Assignment 4 (Data Wrangling & Data Visualization) </h1>

<a id="top"></a>

## Table of Contents
1. [About the Project](#about)
2. [Getting Started](#getting_started)
   - [Instructions](#instructions)
4. [Sample Problems](#problems)
   - [Problem 1](#P1)
5. [Author](#author)

<a name="about"></a>
## About the Project
- Programming Assignment 4 is about identifying the codes and functions in cleaning and visualizing data. The codes and functions in creating a Python program will be used for data wrangling and data visualization.

<a name="getting_started"></a>
## Getting Started
- To run the given code, follow these instructions:
  
<a name="instructions"></a>
 ### Instructions
 1. Install **Anaconda Navigator** at https://www.anaconda.com/download
 2. Open **Jupyter notebook**
 3. Download and open _Ching_Data_Wrangling-PA4.ipynb_
 4. Run the programs 

<a name="problems"></a>
## Sample Problem:
* For the problem, the following table shows the data set used:

| Name | Gender | Track            | Hometown | Math | Electronics | GEAS | Communication  |
|------|--------|------------------|----------|------|-------------|------|----------------|
| S1   | Male   | Instrumentation  | Luzon    | 58   | 89          | 75   | 78             |
| S2   | Female | Communication    | Mindanao | 52   | 75          | 90   | 52             |
| S3   | Female | Instrumentation  | Mindanao | 83   | 74          | 77   | 57             |
| S4   | Male   | Instrumentation  | Visayas  | 65   | 58          | 91   | 68             |
| S5   | Male   | Communication    | Luzon    | 59   | 86          | 43   | 88             |
| S6   | Female | Microelectronics | Visayas  | 88   | 45          | 86   | 83             |
| S7   | Female | Instrumentation  | Luzon    | 66   | 60          | 60   | 48             |
| S8   | Male   | Instrumentation  | Luzon    | 49   | 81          | 64   | 53             |
| S9   | Male   | Instrumentation  | Luzon    | 50   | 36          | 63   | 42             |
| S10  | Male   | Microelectronics | Mindanao | 80   | 84          | 61   | 44             |
| S11  | Female | Communication    | Visayas  | 48   | 56          | 48   | 67             |
| S12  | Male   | Communication    | Visayas  | 89   | 67          | 84   | 64             |
| S13  | Female | Microelectronics | Luzon    | 88   | 35          | 83   | 43             |
| S14  | Female | Microelectronics | Luzon    | 83   | 77          | 89   | 73             |
| S15  | Female | Microelectronics | Mindanao | 69   | 41          | 40   | 86             |
| S16  | Female | Communication    | Luzon    | 71   | 70          | 87   | 81             |
| S17  | Female | Microelectronics | Mindanao | 81   | 79          | 77   | 45             |
| S18  | Male   | Communication    | Visayas  | 81   | 40          | 81   | 52             |
| S19  | Male   | Microelectronics | Luzon    | 79   | 63          | 79   | 71             |
| S20  | Female | Communication    | Mindanao | 59   | 60          | 62   | 85             |
| S21  | Female | Microelectronics | Visayas  | 83   | 51          | 68   | 72             |
| S22  | Female | Communication    | Visayas  | 64   | 39          | 89   | 58             |
| S23  | Male   | Instrumentation  | Luzon    | 84   | 70          | 74   | 47             |
| S24  | Female | Microelectronics | Visayas  | 85   | 45          | 60   | 41             |
| S25  | Male   | Communication    | Luzon    | 74   | 91          | 94   | 42             |
| S26  | Female | Instrumentation  | Visayas  | 71   | 47          | 83   | 62             |
| S27  | Male   | Microelectronics | Visayas  | 70   | 47          | 40   | 86             |
| S28  | Male   | Communication    | Visayas  | 85   | 53          | 80   | 53             |
| S29  | Male   | Instrumentation  | Mindanao | 73   | 48          | 71   | 62             |
| S30  | Male   | Instrumentation  | Luzon    | 78   | 81          | 57   | 56             |


<a name="P1"></a>
## **ECE BOARD EXAM PROBLEM:**
* Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given. </br>

**Step 1.** Before coding, we must import the Pandas library.
``` python
import pandas as pd
```
</br>

**Step 2.** I loaded the Excel file named 'board2_xlsx' and stored the dataframe to `df` and displayed it in the program. 
``` python
# import the excel file
df = pd.read_excel('board2.xlsx')
df
```
</br>

**PART 1: Data Frame** </br>
* Create the data frames based on the format Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas

#### a. Instru = ["Name", "GEAS", "Electronics >70"]; "Track" is constant as "Instrumentation" and "Hometown" "Luzon" </br>

**Step 3.** Using `.loc`, I performed indexing and specified the rows to locate and the columns that will be displayed in the table. 
``` python
# Locate rows required and columns to display
# Rows:    Track - Instrumentation, Hometown - Luzon, Electronics
# Columns: NAME, GEAS, ELECTRONICS
Instru = df.loc[ 
                (df["Track"] == "Instrumentation") & (df["Hometown"] == "Luzon") & (df["Electronics"]>70), 
                ["Name", "GEAS", "Electronics"]
               ]
Instru
```

**Expected Output**: 
</br> 

|    | Name | GEAS | Electronics |
|----|------|------|-------------|
| 0  | S    | 75   | 89          |
| 7  | S8   | 64   | 81          |
| 29 | S30  | 57   | 81          |

</br>

#### b.  Mindy = ["Name", "Track", "Electronics", "Average >= 55"]; "Hometown" is constant as "Mindanao" and "Gender" "Female"

**Step 4.** For the second table, I used `.mean` for all the subjects to get the average score and added it as a new column.
```python
# Getting the average of the 4 subjects and adding a column "Average" in axis 1
df["Average"] = df[ ["Math","Electronics","GEAS","Communication"] ].mean(axis=1)
```
</br>

**Step 5** Again, I specified the rows to locate and the columns that will be displayed in the table. 
```python
# Locate rows required and columns to display
# Rows:    Hometown - Mindanao, Gender - Female, Average >= 55
# Columns: Name, Track, Electronics, Average
Mindy = df.loc[ 
                (df["Hometown"] == "Mindanao") & (df["Gender"] == "Female") & (df["Average"] >= 55), 
                ["Name", "Track", "Electronics", "Average"]  
              ]
Mindy
```
</br>

**Expected Output**: 
</br>

|    | Name | Track            | Electronics | Average |
|----|------|------------------|-------------|---------|
|  1 | S2   | Communication    | 75          | 67.25   |
|  2 | S3   | Instrumentation  | 74          | 72.75   |
| 14 | S15  | Microelectronics | 41          | 59.00   |
| 16 | S17  | Microelectronics | 79          | 70.50   |
| 19 | S20  | Communication    | 60          | 66.50   |

</br>

<!-- (NEXT PART) -->

**PART 2: Data Visualization** </br>
* Visualization of how different features contrbutes to average grade

**Step 1.** We must import the matplotlib library first.
``` python
# To visualize the data, use matplotlib
import matplotlib.pyplot as plt
```
</br>

**Step 2.** I used `plt.bar` to display a bar graph that relates the Track vs. Average. The other syntaxes simply modify how the output looks.
``` python
# Bar Chart for Track and Average
plt.figure( figsize=(7,5) ) # Size 
plt.bar( df["Track"], df["Average"], zorder = 2 ) # Creates a bar graph
plt.grid(True, zorder=0) # Grid behind the graph
plt.show()
```

**Expected Output**: 
</br></br>
<img width="589" height="428" alt="image" src="https://github.com/user-attachments/assets/84c48a15-a24d-430c-be2c-4e036fda3b13" />
</br>

> [!NOTE]
> The bar graph shows that examinees from the **microelectronics track** had the highest average.
</br>

**Step 3.** I also displayed a bar graph that relates the Gender vs. Average.
``` python
# Bar Chart for Gender and Average
plt.figure( figsize=(7,5) ) # Size 
plt.bar( df["Gender"], df["Average"], zorder = 2 ) # Creates a bar graph
plt.grid(True, zorder=0) # Grid behind the graph
plt.show()
```

**Expected Output**: 
</br></br>
<img width="589" height="428" alt="image" src="https://github.com/user-attachments/assets/052036e9-b42e-4f04-85b2-9fe318b100a3" />
</br>

> [!NOTE]
> The data shows that **female** examinees scored the highest average.
</br>

**Step 4.** Lastly, I displayed a bar graph that relates the Hometown vs. Average.
``` python
# Bar Chart for Hometown and Average
plt.figure( figsize=(7,5) ) # Size 
plt.bar( df["Hometown"], df["Average"], zorder = 2 ) # Creates a bar graph
plt.grid(True, zorder=0) # Grid behind the graph
plt.show()
```

**Expected Output**: 
</br></br>
<img width="589" height="428" alt="image" src="https://github.com/user-attachments/assets/4d8bfbaa-d8c7-4b93-b274-9002e0afa120" />
</br>

> [!NOTE]
> The data shows that examinees from **Luzon** scored the highest average.
</br>

</br>

<a name="author"></a>
## **Author** 
- Name: Elton Ching
- Section: 2ECE-B

<p align="right"> (<a href="#top">Back to Top</a>) </p>
