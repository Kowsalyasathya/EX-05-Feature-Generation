# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM:

### STEP 1

Read the given Data
### STEP 2

Clean the Data Set using Data Cleaning Process
### STEP 3

Apply Feature Generation techniques to all the feature of the data set
### STEP 4

Save the data to the file


# CODE:

Program Developed By : KOWSALYA M
Register Number : 212222230069

### Dataset-1 (data.csv)
```
import pandas as pd
import numpy as np
import seaborn as sbn
import matplotlib.pyplot as plt
df = pd.read_csv("/content/data.csv")
df1 = df.copy()
df1

df.info()
df.isnull().sum()

! pip install --upgrade category_encoders

from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['Ord_2'] = le.fit_transform(df['Ord_2'])
sbn.set(style ="darkgrid")
sbn.countplot(x ='Ord_2', data = df)

from sklearn.preprocessing import OneHotEncoder
enc = OneHotEncoder()
enc = enc.fit_transform(df[['City']]).toarray()
encoded_colm = pd.DataFrame(enc)
df = pd.concat([df, encoded_colm], axis=1)
df = df.drop(['City'], axis=1)
df

df = pd.get_dummies(df, prefix=['Ord_2'], columns=['Ord_2'])
df

df = pd.get_dummies(df, prefix=['Ord_1'], columns=['Ord_1'])
df
```

### Dataset-2 (Encoding data.csv)

```
import pandas as pd
import numpy as np
import seaborn as sbn
import matplotlib.pyplot as plt
df = pd.read_csv("/content/Encoding Data.csv")
df1 = df.copy()
df1.head(5)

df = pd.get_dummies(df, columns = ['bin_1','bin_2'])
df

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder, OneHotEncoder
climate = ['Cold','Warm','Hot']
enc = OrdinalEncoder(categories = [climate])
enc.fit_transform(df1[["ord_2"]])

df1['Ord_2'] = enc.fit_transform(df1[["ord_2"]])
df1

df2 = df1.copy()
le = LabelEncoder()
df2['Nom_0'] = le.fit_transform(df2[["nom_0"]])
df2

df3 = df2.copy()
oe = OneHotEncoder()
oe.fit_transform(df3[["bin_1"]])
df3.head(5)

df4 = df3.copy()
oe = OneHotEncoder()
oe.fit_transform(df4[["bin_2"]])
df4.head(5)

from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['ord_2'] = le.fit_transform(df['ord_2'])
sbn.set(style ="darkgrid")
sbn.countplot(x ='ord_2', data = df)
```
### Dataset-3 (titanic_dataset.csv)

```
import pandas as pd
import numpy as np
import seaborn as sbn
df = pd.read_csv("/content/titanic_dataset.csv")
df.head(5)

#data cleaning
df.info()
df.isnull().sum()

df['Age']=df['Age'] . fillna(df['Age'].mean())
df['Cabin']=df['Cabin']. fillna(df['Cabin']. mode() [0])
df['Embarked']=df['Embarked'] . fillna(df['Embarked'].mode( )[0])
df.isnull().sum()

from sklearn.preprocessing import LabelEncoder
lc = LabelEncoder()
df['Sex'] = lc.fit_transform(df['Sex'])
sbn.set(style ="darkgrid")
sbn.countplot(x ='Sex', data = df)

from sklearn.preprocessing import OneHotEncoder
enc= OneHotEncoder()
enc= enc.fit_transform(df[['Name']]).toarray()
encoded_colm = pd.DataFrame(enc)
df= pd.concat([df, encoded_colm], axis=1)
df= df.drop(['Name'], axis=1)
df

df = pd.get_dummies(df, prefix=['Ticket'] ,columns=['Ticket'])
df

df = pd.get_dummies(df, prefix=['Embarked'] ,columns=['Embarked'])
df.head(10)
```
## OUTPUT:

Data.csv:

![fea1](https://user-images.githubusercontent.com/118671457/233466312-63f24eea-8811-47c4-8406-0efe16793d34.png)
![fea2](https://user-images.githubusercontent.com/118671457/233466346-a2397458-0dc7-4315-ad0b-28e5a72ce235.png)
![fea3](https://user-images.githubusercontent.com/118671457/233466375-f3583f8c-6432-49e9-82d6-2161ffee1d17.png)
![fea4](https://user-images.githubusercontent.com/118671457/233466430-c6fe0bc3-e66f-4e87-9368-27f64dc2c04a.png)
![fea5](https://user-images.githubusercontent.com/118671457/233466498-46c40dd1-6e20-45e0-9708-5e94a0effba7.png)
![fea6](https://user-images.githubusercontent.com/118671457/233466545-7a335ece-ea70-4e8f-8a42-d5b2d8a03904.png)
![fea7](https://user-images.githubusercontent.com/118671457/233466598-eb7ac85d-e37c-468b-aabe-7972f8bd6292.png)

## Encoding.csv :

![fea8](https://user-images.githubusercontent.com/118671457/233466636-fa21dc26-2e4c-49fd-8e09-c4504b947711.png)
![fea9](https://user-images.githubusercontent.com/118671457/233466694-17819fa7-7f6b-4ce8-b425-c19f0dae1c6a.png)
![fea10](https://user-images.githubusercontent.com/118671457/233466782-edbd306a-fa73-4ba3-9d73-5ec9ed60e4ab.png)
![fea11](https://user-images.githubusercontent.com/118671457/233466838-3195f6e7-1bc6-4c62-a23a-6bc8500811db.png)
![fea12](https://user-images.githubusercontent.com/118671457/233466865-8426d696-b072-43ad-81c6-5c187638ca9e.png)
![fea13](https://user-images.githubusercontent.com/118671457/233466935-10211f57-0c1f-4569-b158-10f89c2a4b35.png)
![fea14](https://user-images.githubusercontent.com/118671457/233466989-770c8767-4b0b-4634-84e2-04c6262ad65a.png)

## Titanic.csv :

![fea15](https://user-images.githubusercontent.com/118671457/233467035-d5d7df83-1587-441c-b24a-428690b37045.png)
![fea16](https://user-images.githubusercontent.com/118671457/233467077-7999d3ac-51bc-4043-b35c-302021b0648b.png)
![fea17](https://user-images.githubusercontent.com/118671457/233467106-ea81a92e-74ba-4de6-91d1-cf821ccbcb89.png)
![fea18](https://user-images.githubusercontent.com/118671457/233467134-b9736b53-4cf3-43df-884d-5f7ffe1250e4.png)
![fea19](https://user-images.githubusercontent.com/118671457/233467169-23f3efae-0632-478e-b604-5a3a94b3b993.png)
![fea20](https://user-images.githubusercontent.com/118671457/233467191-096e4cc5-4299-4d62-8282-e9882a987181.png)

## RESULT:

Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.


