# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

## Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

## ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file

## CODE
```
Program Developed: Dharshini D.S
Register number:212221230022
```
### Data.csv:
```
import pandas as pd
df=pd.read_csv("data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()


df1["City"] = ohe.fit_transform(df1[["City"]])

temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])

edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```
### Data.csv output:
![ds1](https://user-images.githubusercontent.com/93427345/195565371-5b0f62a0-9d59-443a-b18a-1aebab1d594f.png)

![ds2](https://user-images.githubusercontent.com/93427345/195565421-0b68b926-5cc5-425e-919e-65867f44baf4.png)

![ds3](https://user-images.githubusercontent.com/93427345/195565451-ae75ff4c-4d91-4433-8723-3b31c53a75bf.png)

![ds4](https://user-images.githubusercontent.com/93427345/195565496-f356d55e-5c5d-46eb-b5d0-643dd645289b.png)

![ds5](https://user-images.githubusercontent.com/93427345/195565555-827b3c2d-7358-4568-b913-009162e90104.png)

![ds6](https://user-images.githubusercontent.com/93427345/195565577-66f19e9d-1772-438f-9f38-4da924153a01.png)

![ds7](https://user-images.githubusercontent.com/93427345/195565612-5e5d7c66-8bc8-4e61-8d48-63dbe1fad175.png)

### Encoding.csv code:
```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()

df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])

df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4
```
### Encoding.csv Output:
![1](https://user-images.githubusercontent.com/93427345/195566163-146b54ce-a766-4899-9de7-7932f5a59dff.png)

![2](https://user-images.githubusercontent.com/93427345/195566234-2e905f05-7c18-4f12-8aad-7e9f0db8ff56.png)

![3](https://user-images.githubusercontent.com/93427345/195566342-41b7d1aa-3f02-4a09-b7f5-0f8090d95307.png)

![4](https://user-images.githubusercontent.com/93427345/195566391-97a65d56-1b68-4987-84da-1219ae2d7fe6.png)

![5](https://user-images.githubusercontent.com/93427345/195566408-09b6f6ed-3602-4d48-a1c7-80fe700d48d3.png)

![6](https://user-images.githubusercontent.com/93427345/195566431-a7ff06b8-be86-4e3d-b149-2e346e6d3414.png)

![7](https://user-images.githubusercontent.com/93427345/195566454-eba9e5d5-ab32-45f4-9d7e-64e4df520512.png)

### Tiatanic.csv Code:
```
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

#removing unwanted data
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)

#data cleaning
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])

df.isnull().sum()

df

#feature encoding
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
ndf=be.fit_transform(df["Sex"])
ndf

df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5
```
### Titanic.csv Output:
![1a](https://user-images.githubusercontent.com/93427345/195567108-7c830b0b-8d7f-455c-9292-294b346d951c.png)

![1b](https://user-images.githubusercontent.com/93427345/195567142-498ffc60-f608-4bc3-bf4a-87c23cc4612a.png)

![1c](https://user-images.githubusercontent.com/93427345/195567161-9326f2d7-037b-4c62-8056-ad66d3077cde.png)

![1d](https://user-images.githubusercontent.com/93427345/195567187-fcd7fe38-43d3-4cb2-ae13-73b83652dde3.png)

![1e](https://user-images.githubusercontent.com/93427345/195567212-496db46c-f5d5-4f9e-b015-1663e51300ff.png)

![1f](https://user-images.githubusercontent.com/93427345/195567233-5aeedabd-921a-4308-9ac1-e1a53eee0cd2.png)

![1g](https://user-images.githubusercontent.com/93427345/195567273-d540d2bf-7596-4393-bded-77eb264ed080.png)

![1h](https://user-images.githubusercontent.com/93427345/195567305-e868e965-3c58-4ed4-ad65-152c74608a2a.png)

## RESULT:
Hence Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.
