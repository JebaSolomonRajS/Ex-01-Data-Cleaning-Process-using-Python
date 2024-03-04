# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

```
### Developed By: Jeba Solomon Raj S
### Register Number: 212223230089
```

### 1) Read and display DataFrame
```Python
import pandas as pd
df=pd.read_csv('/content/SAMPLEDS.csv')
df
```
      
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/b335322f-1fca-41f3-8aae-9e68ab34943c)
</td>
</tr>
<tr>
  <td width=50%>
              
### 2) Display head
```Python
df.head()
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/55cbe44a-d1a7-4658-b43b-488051a3ba80)


### 3) Display tail
```Python
df.tail()
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/4e5a6124-4a84-45cb-bfa3-964d729c04aa)


### 4) Info of datafram
```Python
df.info()
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/5ff82193-4999-4924-b438-42cf465680eb)


### 5) Describe about the dataframe
```Python
df.describe()
```
     
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/02086c41-a894-47c4-8e1f-06c88d3a6dfe)

### 6) Shape of the datafram
```Python
df.shape
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/3b740df0-a40e-49f0-8a76-f3ec7df3bc75)


### 7) Checking tha NUll values
```Python
df.isnull().sum()
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/1004fccf-a655-4cc7-b376-4ee0af446f75)


### 8) Drop the Null values
```Python
x=df.dropna(how='any')
x
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/4adcd2f4-5b54-48d0-9c12-644c7460db50)


### 9) Drop the Null values in Total
```Python
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/4172fc2d-90dd-4020-ace6-042263804e9f)


### 10) FIll the Null values
```Python
df.fillna(0)
```
       
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/4053ca55-b8e1-40f4-b6a1-64c68b371b32)

### 11) Finding the mean value
```Python
mn=df.TOTAL.mean()
mn
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/8f4c67ed-3a78-4687-98e1-ff46f38dd777)


### 12) Fill Null value with Mean value
```Python
df.head()
```
              
#### OUTPUT:

df.TOTAL.fillna(mn,inplace=True)
df


### 13) Final output
```Python
for x in df.index:
  if df.loc[x,"AVG"]>100:
    df.drop(x,inplace=True)
df
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/145bb04e-4c79-4b63-add9-8be28b437332)

### 14) Outlier detection and removal
```Python
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
dff=pd.DataFrame(age)
dff
```
              
#### OUTPUT:
![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/f2616193-f511-4196-bdca-9ccffdd01254)

### 15) Boxplot
```Python
dsf=sns.boxplot(dff)
```
     
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/2bd5dd62-725c-4fa4-83e7-176cd441e254)


### 16) Scatterplot
```Python
dsf=sns.scatterplot(dff)
```
   
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/ed6eb517-e6c2-485a-a7aa-4408df8b2699)


### 17) IQR
```Python
q1=dff.quantile(0.25)
q2=dff.quantile(0.5)
q3=dff.quantile(0.75)
iqr=q3-q1
iqr
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/081147e9-2536-4611-8e0b-7c1c1cdf1fd4)

    
### 18) Checking the high and low value
```Python
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/5757c6fc-0597-4fdd-811e-51979c6b2060)

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/b0d92d4e-80b0-4897-8b58-2341121d269a)



### 19) Filtering outlier value
```Python
dff=dff[((dff>=low)&(dff<=high))]
dff
```
     
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/1f80062c-7eaa-47ce-a48f-9c4ca269fc34)

    
### 20) Dropping the null value
```Python
dff.dropna()
```

              
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/60f37814-2b73-4cd5-b5c4-dc2f727baf1d)


    
### 21) Box plotting after filtering outlier
```Python
sns.boxplot(data=dff)
```
     
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/be407782-7c66-4d35-aa92-ad409beb39b0)

  
### 22) Z Score
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```
 
#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/1289facd-94ac-4ee1-bb9c-06c0f032ef22)

### 23) Z Score
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```

#### OUTPUT:

![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/5b2d2b80-30ba-4d35-860f-bb70f1830826)

   
### 24) Z Score
```Python
sns.boxplot(data=ds)
```

              
#### OUTPUT:
![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/f7db7ba1-3fa2-4f37-af7c-b3b78fde1495)

    
 ### 25) Z Score
```Python
z=np.abs(stats.zscore(ds))
z
```
   
#### OUTPUT:
![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/ff2b6968-ffb5-4d96-91fd-8f5b047d1489)



### 26)Z score 
```Python
print(ds[z['weight']>3])
```


#### OUTPUT:
![image](https://github.com/JebaSolomonRajS/Ex-01-Data-Cleaning-Process-using-Python/assets/139432449/b91f9d4c-fd3f-4647-bdb3-ccb61b00ce5d)


# Result
          Therefore program was successfully executed
