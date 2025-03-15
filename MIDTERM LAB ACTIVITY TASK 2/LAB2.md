# Welcome to LAB 2 #

For today, the user will show how the data is cleaned by using the power query 
******

# Before(For better view, click the picture)**
1. Stretch rows and columns
2. Long Description
3. Having Invalid Data in the Columns like N/A, null and -1 in a string and numerical type columns (For context, Salary, Size, Competition, Industry)
4. Having spammed words in each columns 

<img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20ACTIVITY%20TASK%202/Screenshot%20(48).png" alt="Image Description" width="600" style="float: right; margin-left: 50px;" />

********
# Cleaning the Data 
1. Adjust the Stretched rows and columns
2. Extract your columns then create another column
3. Split the Columns of Salary and Size by delimiter
4. Remove the invalid words that the creator mentioned above
5. Remove the description
6. Done

<img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20ACTIVITY%20TASK%202/Screenshot%20(56).png"/>

# Sorting the Data 
1. Make a duplicate from the original data (e.g: **Original Data na ginawa mo**)
2. Select a specific column then delete the rest of the columns
3. Transforms your numbers into Currency, then multiply by 1000
4. Group the column you selected and get the average using Group By in Transform Menu 
5. Done

Sample: 
1. # Salary By Role Type
  <img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20ACTIVITY%20TASK%202/Sal%20by%20Role%20Type%20(2).png"/>

2. # Salary by Size
  <img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20ACTIVITY%20TASK%202/Salary%20by%20Size%20(sorted).png"/>

3. # Salary by State
  <img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20ACTIVITY%20TASK%202/Salary%20by%20State%20(sorted).png"/>

4. # Salary by Role Type and size
   <img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20ACTIVITY%20TASK%202/Salary%20by%20Role%20and%20Size%20(Sorted).png"/>

# Appendix 
> For users want to prefer to clean the data or query is not available in any versions, check the link below the mentioned cleaning tips that will be used manually:
[LAB 1](https://github.com/EDILBERTOGEMINIANO/edilbertogemini/tree/main/MIDTERM%20LAB%20TASK%201#appendix-frequently-asked-questions)

1. **Duplicate the sheets**
   - Right-Click the sheet you choose
   - Select Move or Copy
   - Done

2. **Remove Other Categories from a specific column**
   - Use the **ctrl** key to select what data you want to keep, then press **Ctrl + C**
   - Create a new sheet
   - Paste your selected columns by pressing **Ctrl + V**
   - Done

3. **Merge Queries manually**
   - Sort both sheets
   - Copy your data from the existring sheet, then paste
   - Done 
