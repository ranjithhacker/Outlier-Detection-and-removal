# Ex-02_DS_Outlier_Detection_and_Removal
# AIM
To detect and remove the outliers in the given data set and save the final data.

# Explanation
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM
## STEP 1
Import the required packages(pandas,numpy,scipy)
## STEP 2
Read the given csv file
## STEP 3
Convert the file into a dataframe and get information of the data.
## STEP 4
Remove the non numerical data columns using drop() method.
## STEP 5
Detect the outliers in the data set using z scores method.
## STEP 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
## STEP 7
Check if the outliers are removed from data set using graphical methods.
## STEP 8
Save the final data set into the file

# CODE
```
/* 
Name : Ranjith G.
Register Number : 212220220034
**Removing Outliers - bhp.csv**
import pandas as pd
import numpy as np
df = pd.read_csv('/content/bhp.csv')
df.head(10)
df.boxplot()
df.shape
q1=df.price_per_sqft.quantile(0.25)
q3=df.price_per_sqft.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df[(df.price_per_sqft<lower_limit)|(df.price_per_sqft>upper_limit)]
df[(df.price_per_sqft<=lower_limit)&(df.price_per_sqft>=upper_limit)]
df = df.drop(["location","size","bhk"],axis=1) 
from scipy import stats
z=np.abs(stats.zscore(df))
z
df2=df.copy()
df2=df2[(z<3).all(axis=1)]
df2
df2.boxplot()

**Removing Outliers - height_weight.csv**
import pandas as pd
import numpy as np
df1 = pd.read_csv('/content/height_weight.csv')
df1.head(10)
df1.drop("gender",axis=1)
df1.boxplot()
q1=df1.weight.quantile(0.25)
q3=df1.weight.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df1_new=df1[(df1.weight<lower_limit)&(df1.weight>upper_limit)]
df1_new.boxplot()
q1=df1.height.quantile(0.25)
q3=df1.height.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df1_new=df1[(df1.weight<lower_limit)&(df1.weight>upper_limit)]
df1_new.boxplot()
*/
```
# OUPUT
## Removing Outliers - bhp.csv
![Removing Outliers](/images/img1.png)
![Removing Outliers](/images/img2.png)
## Using IQR method to remove Outliers of price_per_sqft
![Removing Outliers](/images/img3.png)
## Removing non-numerical columns
![Removing Outliers](/images/img4.png)
## Using z-score of 3 method to remove Outliers of price_per_sqft
![Removing Outliers](/images/img5.png)
![Removing Outliers](/images/img6.png)

## Removing Outliers - height_weight.csv
![Removing Outliers](/images/imag1.png)
## Removing non numerical columns
![Removing Outliers](/images/imag2.png)
![Removing Outliers](/images/imag3.png)
## Removing Outliers of weight using IQR
![Removing Outliers](/images/imag4.png)
## Removing Outliers of height using IQR
![Removing Outliers](/images/imag5.png)
# RESULT
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
