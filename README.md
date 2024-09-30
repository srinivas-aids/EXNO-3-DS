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
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/5860e093-2599-483b-aeb6-c5f5e5c71e76)

#ORDINAL ENCODER
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[['ord_2']])

![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/a25d343b-2bf1-486f-a0f5-38d5394cf98c)

df['bo_2']=e1.fit_transform(df[['ord_2']])
df
![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/1fa0112c-6d36-4c25-b64b-bf522d25fda3)

#LABEL ENCODER
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc

![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/6754cd2e-2c31-4184-bf98-ae252df49972)


from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))

df2=pd.concat([df,enc],axis=1)
df2

![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/cfa63758-68d3-4fdb-944e-295ba16206ab)

pd.get_dummies(df2,columns=['nom_0'])


![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/11397ace-166b-41d4-a847-200aad7a4b4d)


from category_encoders import  BinaryEncoder
df=pd.read_csv("/content/data.csv")
df

![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/987488dc-1f67-4863-b0cb-5daa4df3ec91)

be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb


![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/59bed686-15b3-4eff-a52a-baa4c054f3a3)


from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc['City'],y=cc['Target'])
cc=pd.concat([cc,new],axis=1)
cc

![image](https://github.com/Preetha-Senthamilan/EXNO-3-DS/assets/119390282/eeb52a17-05c6-4387-a18c-e9f8bdd2c588)











     
# RESULT:
     
Thus, performing Feature Encoding and Transformation process for the given data set is completed.
       
