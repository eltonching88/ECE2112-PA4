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

**Step 3** Using `.loc`, I performed indexing and specified the rows to locate and the columns that will be displayed in the table. 
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

**Step 4** 
```python
# Getting the average of the 4 subjects and adding a column "Average" in axis 1
df["Average"] = df[ ["Math","Electronics","GEAS","Communication"] ].mean(axis=1)
```
</br>

**Step 5** 
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
| 1  | S2   | Communication    | 75          | 67.25   |
| 2  | S3   | Instrumentation  | 74          | 72.75   |
| 14 | S15  | Microelectronics | 41          | 59.00   |
| 16 | S17  | Microelectronics | 79          | 70.50   |
| 19 | S20  | Communication    | 60          | 66.50   |

</br>

<!-- (NEXT PART) -->

## **Problem 2**
* 

**Step 1.** Again, we must import the Pandas library first.
``` python
import pandas as np
```
</br>

**Step 2.** I loaded the pre-installed file named 'cars.csv' and stored the data to `cars` 
``` python
# Load the csv file in the same folder
cars = pd.read_csv('cars.csv')
```
</br>

**Step 3.** For Part A, I located the first five rows with odd-numbered columns using `.iloc[]`. The range for rows is index [0:5] and displays only rows 1 to 5. The range for columns is [0:13:2], which is a range of index [0:13] with an increment of 2 to only display the odd-numbered columns.
``` python
# a. Locates and displays the first five rows with odd columns
cars.iloc[ 0:5, 0:13:2 ]
```
**Expected Output**: 
<p align="center">
  <img src="P2_TableA.png" alt="P2 Table A" width="350">
</p>

<!--
| Model               | cyl |  hp |  wt   | vs | gear |
|---------------------|-----|-----|-------|----|------|
| Mazda RX4           | 6   | 110 | 2.620 | 0  | 4    |
| Mazda RX4 Wag       | 6   | 110 | 2.875 | 0  | 4    |
| Datsun 710          | 4   | 93  | 2.320 | 1  | 4    |
| Hornet 4 Drive      | 6   | 110 | 3.215 | 1  | 3    |
| Hornet Sportabout   | 8   | 175 | 3.440 | 0  | 3    |
-->

</br>

**Step 4.** For Part B, I located the model 'Mazda RX4' using `.loc`. The IF condition in this function is to only locate 'Mazda RX4' in the row 'Model' and display the entire row.
``` python
# b. Locates and displays the row that contains the ‘Model’ of ‘Mazda RX4’.
cars.loc[ cars['Model'] == 'Mazda RX4' ]
```
**Expected Output**: 
<p align="center">
  <img src="P2_TableB.png" alt="P2 Table B" width="450">
</p>
</br>

**Step 5.** For Part C, I located the model 'Camaro Z28' and column 'cyl' using `.loc`. The IF condition in this function is to only locate 'Camaro Z28' in the row 'Model' and 'cyl' in the columns. I added `.values[0]` to only display the value asked.
``` python
# c. Locates 'Camaro Z28' and 'cyl' and returns the value of 'cyl'
n = cars.loc[ cars['Model'] == 'Camaro Z28', 'cyl' ].values[0]
print(n)
```
**Expected Output**: 
```
8
```

**Step 6.** For Part D, I stored 'Mazda RX4 Wag', 'Ford Pantera L', and 'Honda Civic' and column 'cyl' in the variable `models`. Then, I modified the index to only select 'Model' using `set_index()`. Using `.loc[]`, it will output the rows in 'models' and columns in 'cyl' and 'gear' only.
``` python
# d. Locates the models and outputs 'cyl' and 'gear'
models = ['Mazda RX4 Wag', 'Ford Pantera L', 'Honda Civic'] # Choose elements manually
MD = cars.set_index("Model")     # Set what column to look at
MD.loc[models, ["cyl", "gear"]]  # Output selected models and
```
**Expected Output**: 
<p align="center">
  <img src="P2_TableD.png" alt="P2 Table D" width="200">
</p>

</br>

<a name="author"></a>
## **Author** 
- Name: Elton Ching
- Section: 2ECE-B

<p align="right"> (<a href="#top">Back to Top</a>) </p>
