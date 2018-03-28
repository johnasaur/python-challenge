

```python
# import dependencies
import os
import csv
```


```python
election_file = os.path.join("../Lesson-Plans/election_data_1.csv")
```


```python
#dictionary for vote count and candidates
votes = {}
```


```python
#set all votes to zero
all_votes = 0
```


```python
# read file
with open(election_file, "r") as csvfile:
    csvread = csv.reader(csvfile)
    # skip header
    next(csvread, None)
    for row in csvread:
        all_votes += 1
        if row[2] in votes.keys():
            votes[row[2]] = votes[row[2]] +1
        else:
            votes[row[2]] = 1
```


```python
# list for candidates and vote count
candidates = []
votes_count = []
```


```python
# keys to lists
for key, value in votes.items():
    candidates.append(key)
    votes_count.append(value)
```


```python
#create vote percentage
vote_percentage = []
for y in votes_count:
    vote_percentage.append(round(y/all_votes * 100, 2))
```


```python
# zip data in a file
zip_file = list(zip(candidates, votes_count, vote_percentage))
```


```python
# winner info
winners = []
for w in zip_file:
    if max(votes_count) == w[1]:
        winners.append(w[0])
```


```python
# winner str
winners2 = winners[0]
```


```python
# to text file
text_file = os.path.join("../Lesson-Plans/election.txt")
```


```python
# write results 
with open(text_file, "w") as filewrite:
    filewrite.writelines("Election Results\n")
    filewrite.writelines("-----------------------------" + "\n")
    filewrite.writelines("Total Votes: " + str(all_votes) + "\n")
    filewrite.writelines("-----------------------------" + "\n")
    filewrite.writelines(str(candidates) + ": " + str(vote_percentage) + "% (" + str(votes_count) + "\n")
    filewrite.writelines("------------------------------" + "\n")
    filewrite.writelines("Winner: " + str(winners2) + "\n------------------------------")
        
```


```python
# print to terminal
with open(text_file, "r") as readfile:
    print(readfile.read())
```

    Election Results
    -----------------------------
    Total Votes: 803000
    -----------------------------
    ['Vestal', 'Torres', 'Seth', 'Cordin']: [48.0, 44.0, 5.0, 3.0]% ([385440, 353320, 40150, 24090]
    ------------------------------
    Winner: Vestal
    ------------------------------

