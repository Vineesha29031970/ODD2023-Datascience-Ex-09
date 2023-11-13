# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE AND OUTPUT
```
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
print (df)
```
<img width="365" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/99db2ca5-afc7-40ac-94a9-6fbc22a2ef13">

```
df.isnull().sum()
```

<img width="143" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/9b9e12ec-efb4-493a-97c4-2ddfb2b7db3d">

# FINDING OUTLIERS
```
plt.figure(figsize=(5,5))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
<img width="348" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/81ba2bf2-4aa0-458b-9bb6-c7e0c3938df3">

# REMOVING OUTLIERS

```
plt.figure(figsize=(5,5))
cols=['total_bill','tip','size']
Q1=df[cols].quantile(0.25)
Q3=df[cols].quantile(0.75)
IQR=Q3-Q1
df=df[-((df[cols]<(Q1 - 1.5 * IQR))[df[cols]>(Q3 + 1.5 + IQR)]).any(axis=1)]
df.boxplot()
plt.show()
```

<img width="379" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/9f392fac-6343-47f0-a45b-fb0991d8aa83">


# 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount of day of the week")
plt.show()
```
<img width="462" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/621d2166-9a13-4ecc-834a-e505e35ac5d6">

# 2.What is the average tip amount given by smokers and non-smokers?
```
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Averaga tip amount given by somkers and non-smokers")
```

<img width="457" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/bf84eb3f-5ca1-4622-a678-f2cd8182ea38">

# 3.How does the tip percentage vary based on the size of the dining party?
```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip percentage by dining party size")
```
<img width="430" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/483a8266-4a18-4d8c-a13f-34b6e63ea87e">


# 4.Which gender tends to leave higher tips?

```
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips based on gender")
```

<img width="444" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/fe9d39af-a478-47b7-aa85-faa5e093398e">


# 5.Is there any relationshio between the bill amount and the day of the week?

```
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```
<img width="460" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/cf752c1e-ddec-488f-9ced-3ca7accbcb3f">

# 6.How does the distribution of total billa mounts vary across different time periods(lunch vs. dinner)?
```
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of total bill amounts by time of day")
plt.show()
```
<img width="440" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/2c328e4b-9b95-4491-a794-ad9080aab29e">

# 7. Why dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total bill amount by dining party size")
plt.show()
```

<img width="437" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/08799f68-d995-4c53-a181-ab62c3ba5669">


# 8.What is the distribution of tip amounts for each day of the week?

```
sns.boxplot(x="day",y="tip",data=df)
plt.title("Tip amount by day of week")
plt.show()
```


<img width="430" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/ed822bfd-284b-4a61-8126-46dda5e05136">

# 9.How does the tip amount vary based on the type of service (lunch vs. dinner)?
```
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip amount by time of day")
plt.show()
```

<img width="427" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/51994d1f-c5e1-4b95-b0d7-2591eb972519">

# 10.Is there any correlation between the total bill amount?
```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between tip amount and totalbill amount")
plt.show()
```

<img width="449" alt="image" src="https://github.com/Vineesha29031970/ODD2023-Datascience-Ex-09/assets/133136880/d4139808-32c4-42b2-8059-4c52657e8f49">

# RESULT
Thus the Data Visualization on a complex dataset is performed and saved the data to a file.
