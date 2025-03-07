## Midterm Task 1: Data Cleaning and Preparation in Excel 
* For this Midterm Task, the creator will show how to clean and remove any unnecessary elements in your data using the Excel tricks 
## Before: (for much larger view, click the link)
1. The cells are stretched to each other, leading to the readers confused 
2. Having inf in the quality and price which is doesn't exist in general view of money
3. Each cells in Rating columns and Location columns have unnecessary data shown that leads to confusion among the readers

<img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20TASK%201/uncleaned%20.png" alt="Image no.1" width="500" height="200" />
<div style="picture-align: right;">

****
## Steps To Clean The Data 
1. Autofit Rows and Columns
2. Remove the Duplicates using Find and Replace
3. Trim Extra Spaces using **TRIM Formula** then copy your adjusted spaces into new column but paste it as values to prevent errors 
4. Change the Blank Cells into TBA using **Find and Replace**
5. Spell Check
6. Handle the Errors using **IFERROR Formula**
7. To Look  like 1,000, Select the **Number Format** then use the number seperator from Number Category
   - To Transform the shorter dates, Format all the cells in the Date Column into Short Date 

8. Replace the 'inf' to blank Using Find and Replace

Now your database looks like this 

<img src="https://github.com/EDILBERTOGEMINIANO/edilbertogemini/blob/main/MIDTERM%20LAB%20TASK%201/Screenshot%20(52).png" alt="Image no.1" width="500" height="300" />
<div style="picture-align: right;">

****
## Appendix (Frequently Asked Questions)
   1. _Find and Replace_

      1. Select the column and apply a Filter (Ctrl + Shift + L).
      2. Filter the values you want to replace.
      3. Select the visible filtered cells (Ctrl + G → Special → Visible Cells Only).
      4. Use Ctrl + H to find and replace only in the selected cells.
      5. In the Find what box, enter the value you want to find.
      6. In the Replace with box, enter the new value.

  
2.  _Autofitting the Rows and Columns_

     1. Select the rows or columns you want to AutoFit.
     2. Go to the Home tab.
     3. Click Format (under the "Cells" group).
     4. Choose AutoFit Column Width or AutoFit Row Height.
    

3. _Using the TRIM Formula_

    - The TRIM function in Excel removes all extra spaces from text, leaving only single spaces between words.
    - Format: TRIM(Text)
    - Reminder: TRIM only removes extra spaces; it does not remove non-breaking spaces.

5. _Using Number Format_
   
     1. Select the cells or range you want to format.
     2. Press Ctrl + 1 to open the Format Cells dialog.
     3. Go to the Number tab.
     4. Choose the desired format.

6. _Using IFERROR Formula_
     - The IFERROR function helps handle errors in Excel formulas by returning a custom value when an error occurs.
     - **Format**: =IFERROR(value, value_if_error)
       - value :  The formula or expression to evaluate
       - value_if_error → The result to return if an error occurs.
     1. Select a cell where you want to apply the formula.
     2. Type the what type of error in the formula.
        - **Sample Format**: =IFERROR( [@Quantity]*[@[Price Per Unit]] , "")
     3. Then Press **ENTER**
   

   
       



       
