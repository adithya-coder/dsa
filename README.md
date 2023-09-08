```python
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
```


```python
raw_data=pd.read_csv("loan.csv")
```


```python
raw_data.head()
```





```python
aw_data.shape
```




    (20000, 142)




```python
raw_data.dtypes
`



```python
raw_data['loan_amnt'].describe()


```python
raw_data= raw_data.drop(['zip_code', 'policy_code', 'application_type', 'last_credit_pull_d',
'verification_status', 'pymnt_plan', 'funded_amnt_inv', 'sub_grade', 'out_prncp',
'out_prncp_inv', 'total_pymnt_inv', 'total_pymnt', 'total_pymnt_inv', 'total_rec_prncp',
'total_rec_int', 'total_rec_late_fee', 'recoveries', 'collection_recovery_fee', 'last_pymnt_d',
'last_pymnt_amnt', 'initial_list_status'], axis =1)
```


```python
raw_data.shape
```




    (20000, 122)




```python
col_num=0
TotalObjects = raw_data.shape[0]
print ("Column\t\t\t\t\t Null Values%")
for x in raw_data:
	nullCount = raw_data[x].isnull().sum();
	nullPercent = nullCount*100 / (TotalObjects)
	if nullCount > 0 and nullPercent > 20 :
		col_num=col_num+1
		raw_data.drop(x, axis=1,inplace=True)
		print(str(x)+"\t\t\t\t\t"+str(nullPercent))
print ("A total of "+str(col_num)+" deleted !")
```


```python
raw_data.shape


```python
raw_data['emp_title'].fillna('Unknown',inplace = True)
```


```python
raw_data['dti'].fillna(0,inplace=True)
```


```python
raw_data['revol_util'].fillna(raw_data['revol_util'].mean(),inplace = True)

```


```python
pd.unique(raw_data['emp_length'].values)
```




    array(['10+ years', '6 years', '4 years', '< 1 year', '2 years',
           '9 years', nan, '5 years', '3 years', '7 years', '1 year',
           '8 years'], dtype=object)




```python
raw_data['emp_length'].fillna(0,inplace=True)
```


```python
pd.unique(raw_data['emp_length'].values)
```




    array(['10+ years', '6 years', '4 years', '< 1 year', '2 years',
           '9 years', 0, '5 years', '3 years', '7 years', '1 year', '8 years'],
          dtype=object)




```python

```

# lab 2

```python
import pandas as pd
from apyori import apriori 
```


```python
data = pd.read_csv('movie_dataset.csv',header=None)
display(data.head())
```




```python
 = data.values.tolist()
records = []
for i in range(1, 7501):
    records.append([str(data.values[i, j]) for j in range(0, 20)])
```

```python
num_transactions = len(transactions)
min_support_percent = 1
num_transactions
```

```python
min_support =(min_support_percent / 100) * num_transactions
print(min_support)


```python

association_rules = apriori(records, min_support=0.01,min_lift=3)

rs=list(association_rules)

```python
for item in rs:
    print("Rule:", item.items)
    print("Support:", item.support)
```
# lab 3

```python
import pandas as pd
from apyori import apriori
```


```python
store_data = pd.read_csv("store_data.csv",header=None)
display(store_data.head())


records = []
for i in range(1, 7501):
    records.append([str(store_data.values[i, j]) for j in range(0, 20)])
```


```python
association_rules = apriori(records, min_support=0.0045, min_confidence=0.2,min_lift=3, min_length=2)
association_results = list(association_rules)
```


python
for item in association_results:
    print("Rule:", item.items)
    print("Support:", item.support)
   
python
store_data.shape

``` lab 4

import libries 
import pandas as pd
 use classifer and split libry fro, sklearn library
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
import the data set

data_zoo = pd.read_csv("zoo.csv")

see first five raws
data_zoo.head()

see raws and columns
data_zoo.shape

 assign 1 - 17 data set into x variable
x = data_zoo.iloc[:,1:17]
x.shape
 assign last column to the y variable

y = data_zoo.iloc[:,17]
when only one column not show the column number
y.shape

first five y data
y.head()

first five x data
x.head()
devide data set to train and test 
test data part size is 0.25

x_train,x_test,y_train,y_test = train_test_split(x,y, test_size=0.25)
view the x_train size
x_train.shape

view the x_test size
x_test.shape

75 raws for train
only one column
y_train.shape

25 raws for test
only one column
y_test.shape

build the classfier
zoo_classifier = DecisionTreeClassifier(random_state=0)
zoo_classifier

train the classifer using train data set x
zoo_classifier.fit(x_train,y_train)

test the accuracy using x_test and y_test
zoo_classifier.score(x_test,y_test)
ake prediction

predict command is use
zoo_classifier.predict(x_test[10:15])

see the result
y_test[10:15]  ```


