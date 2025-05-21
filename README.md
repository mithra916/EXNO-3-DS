## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
      import pandas as pd
      df=pd.read_csv("/content/Encoding Data (1).csv")
      df
```
![image](https://github.com/user-attachments/assets/42664842-cb37-4ab6-8730-1a666e790509)

```
     from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
     pm=['Hot','Warm','Cold']
     e1=OrdinalEncoder(categories=[pm])
     e1.fit_transform(df[["ord_2"]])
```

![image](https://github.com/user-attachments/assets/2d8c76b0-c435-435e-a366-089da18be8ee)

```
    df['bo2']=e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/user-attachments/assets/1d5e13f7-6431-400a-82de-82cfecefce59)

```
     le=LabelEncoder()
     dfc=df.copy()
     dfc['ord_2']=le.fit_transform(dfc['ord_2'])
```
![image](https://github.com/user-attachments/assets/41ec0963-2a04-4571-8bd4-b813f61c0a4d)

```
       from sklearn.preprocessing import OneHotEncoder
       ohe=OneHotEncoder(sparse=False)
       df2=df.copy()
       enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
```
![image](https://github.com/user-attachments/assets/a8545271-3d56-4d48-9bf6-10fe4807ef50)

```
      df2=pd.concat([df2,enc],axis=1)
```
![image](https://github.com/user-attachments/assets/c5be0cea-71dc-42bf-8a22-763e88df3d1f)

```
         from category_encoders import BinaryEncoder
         df=pd.read_csv("/content/data.csv")
         be=BinaryEncoder()
         nd=be.fit_transform(df['Ord_2'])
         dfb=pd.concat([df,nd],axis=1)
         dfb1=df.copy()
```
![image](https://github.com/user-attachments/assets/1c70f1b8-3e12-429d-99a9-646077e22c15)

```
         from category_encoders import TargetEncoder
         te=TargetEncoder()
         cc=df.copy()
         new=te.fit_transform(X=cc["City"],y=cc["Target"])
         cc=pd.concat([cc,new],axis=1)
```
![image](https://github.com/user-attachments/assets/2f6fbc47-3b28-4545-a004-5bc95b03e121)

![image](https://github.com/user-attachments/assets/26c861cd-8753-43b6-857c-25195d7872f1)

![image](https://github.com/user-attachments/assets/ae853d78-a1c2-4cfa-ac18-6f50b6fe4264)

![image](https://github.com/user-attachments/assets/3a054cae-50bc-4f15-b81d-a70359ea1434)

```
df["Higly Positive Skew_borcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
```
![image](https://github.com/user-attachments/assets/d1c37808-1c4c-4dee-be08-67f5e8f61c73)

```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
```
![image](https://github.com/user-attachments/assets/9cba2e44-ecf0-481a-8e0e-6c074b4f0f55)

```
         from sklearn.preprocessing import QuantileTransformer
         qt=QuantileTransformer(output_distribution='normal')
```
![image](https://github.com/user-attachments/assets/959013f4-83fa-4384-90e9-01f25e5a78ad)

![image](https://github.com/user-attachments/assets/4bde3241-2a65-4db9-a799-493b56f16486)

![image](https://github.com/user-attachments/assets/34c5ad6b-84c6-4036-ad47-31e603216f76)

![image](https://github.com/user-attachments/assets/e38055c2-8f5a-4d56-91eb-01e38063dad8)

![image](https://github.com/user-attachments/assets/729fca60-1af9-4342-a745-b4f27a4e1ede)

![image](https://github.com/user-attachments/assets/1919155d-dacb-4761-875f-b9dc7306b269)

# RESULT:
Thus To read the given data and perform Feature Encoding and Transformation process and save the data to a file has successfully executed
