

```python
import os
import csv
```


```python
bank_file = os.path.join("../Lesson-Plans/budget_data_2.csv")
```


```python
# months and revenues list
months_amount = []
revenue = []
```


```python
# retrieve the file to read csv
with open(bank_file, "r") as csvfile:
    csvread = csv.reader(csvfile)
    # add up all rows via loop sans header
#skip header
    next(csvread, None)
    for rows in csvread:
        months_amount.append(rows[0])
        revenue.append(int(rows[1]))
```


```python
# find all months
all_months = len(months_amount)
```


```python
# set all revenue to zero
max_inc = revenue[0]
max_dec = revenue[0]
all_revenue = 0
```


```python
# compare most increased and most decreased each month; need to total the revenue 
for y in range(len(revenue)):
    if revenue[y] >= max_inc:
        max_inc = revenue[y]
        max_inc_month = months_amount[y]
    elif revenue [y] <= max_dec:
        max_dec = revenue[y]
        max_dec_month = months_amount[y]
    all_revenue += revenue[y]
```


```python
 #average change in revenue
change_avg = round(all_revenue/all_months, 2)
```


```python
#send to text file
file_output = os.path.join("../Lesson-Plans/PyBank.txt")
```


```python
# write results
with open(file_output, "w") as filewrite:
    filewrite.writelines("Financial Analysis\n")
    filewrite.writelines("-----------------------------" + "\n")
    filewrite.writelines("All Months: " + str(all_months) + "\n")
    filewrite.writelines("Total Revenue: " + str(all_revenue) + "\n")
    filewrite.writelines("Average Change in revenue: " + str(change_avg) + "\n")
    filewrite.writelines("Max increase in revenue: " + max_inc_month +  str(max_inc)  + "\n")
    filewrite.writelines("Max decrease in revenue: " + max_dec_month +  str(max_dec) + "\n")
filewrite
```




    <_io.TextIOWrapper name='../Lesson-Plans/PyBank.txt' mode='w' encoding='UTF-8'>




```python
with open(file_output, "r") as readfile:
    print(readfile.read())
```

    Financial Analysis
    -----------------------------
    All Months: 86
    Total Revenue: 36973911
    Average Change in revenue: 429929.2
    Max increase in revenue: Mar-20121141606
    Max decrease in revenue: Sep-2010-1063151
    

