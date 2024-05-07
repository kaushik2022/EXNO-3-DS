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
### Name : BALUREDDY VELAYUDHAM GOWTHAM
### Ref No : 212222040024

```python

import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![ds31](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/a1d22c6b-111e-4d50-bb52-9a304b950efc)


```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
![ds32](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/788545f8-bda0-45d5-854c-5290206fe0c8)


```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
![ds33](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/55b62ac8-3a4f-4218-9b45-3c5bee1f5c84)


```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![d34](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/6418e508-c8fb-418b-94d2-bdcc89baad22)

```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
```

![ds35](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/00e5f154-8c02-4693-ac74-7833f37f64ff)


```
df2=pd.concat([df2,enc],axis=1)
df2
```
![ds36](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/dd06ad93-4fdb-403f-b94b-8dc9fae869b4)


```
pd.get_dummies(df2,columns=["nom_0"])
```

![ds37](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/711027dd-e7cc-4570-998d-8905ab9bba3f)


```
pip install --upgrade category_encoders
```
![ds38](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/1fec0ff5-90a1-4fe1-8d3b-5228175afa4d)

```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```
![ds39](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/e2cdf978-3420-43cc-8b5f-a40bbcdd716e)


```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
df
```
![ds331](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/19cfde1a-9c35-4516-9817-1725dc7619ba)


```
dfb=pd.concat([df,nd],axis=1)
dfb
```
![ds332](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/065286c0-b41a-4d20-ab46-2305e40610a0)


```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```

![ds333](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/96c66379-4259-4dc7-a5d6-c1f7862749ae)

```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```
![ds334](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/94db96c4-093c-4605-b7fb-c803b25abd40)


```
df.skew()
```
![ds335](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/89326b99-8c8c-4b0b-bcb4-c44966598e76)


```
np.log(df["Highly Positive Skew"])
```
![ds336](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/849e1646-779a-4039-96e4-b37f19668f1c)


```
np.reciprocal(df["Moderate Positive Skew"])
```
![ds337](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/add3307f-b9c2-4558-bc0f-917bbc29c286)


```
np.sqrt(df["Highly Positive Skew"])
```
![ds338](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/1ec3e8f3-007f-418c-889e-24cea476de74)


```
np.square(df["Highly Positive Skew"])
```
![ds339](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/c7b575f5-285a-4a5b-ba6d-8b230ac92694)


```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![ds3331](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/3bf2d0f8-1145-4ed5-b8e7-6a0374548fa7)


```
df.skew()
```
![ds3332](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/e99de130-9b5d-4451-956a-085a20b9e342)


```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
```

![ds3332](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/e99de130-9b5d-4451-956a-085a20b9e342)
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/b3935ad8-306b-45a0-bf62-bfba64d1360b)

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
![image](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/d53575f1-bf72-4cbe-8d91-7854216ee0ad)

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
![image](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/bf3745c1-6af3-47a2-a22b-1a505fdcf100)

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/aeb80ae1-d775-4866-a831-8694dd8c2b33)

```
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```

![image](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EXNO-3-DS/assets/119559905/2624d088-9dd7-4552-ae3a-029e411fe900)


## RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.
       
