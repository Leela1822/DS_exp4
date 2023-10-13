# DS_exp4
# Ex-04-Multivariate-Analysis
# AIM:
To perform Multivariate EDA on the given data set.

# EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

# PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')
```
## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)

# OUTPUT:
![image](https://github.com/Leela1822/DS_exp4/assets/106167639/86b6b183-a6e4-469f-bdae-2c944247a0c9)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/f417a253-786c-4b29-bdc1-25f085668de7)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/82afe36b-f38e-4b43-a12a-7ed73b9a1958)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/c5acb250-2f83-439f-baf5-e6e9ee0f3134)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/9d80a7e9-6fd4-4094-8a33-39af57598af7)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/e7fba0be-da80-4843-a38d-beab0009e8c0)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/8947850c-f78d-4cc5-90c6-45b4cab1b97f)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/526338a1-1875-43d5-8457-b0714262b3ba)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/943f30b3-9f8a-4aa2-bbf1-d7f517c1261d)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/9518a167-7756-4164-8801-578234df7729)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/cd6af9c7-168d-4c26-b693-34e476c36658)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/5eb4d9b5-7ee0-45f8-b004-76a32ded6335)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/93df93c5-e8eb-4464-9bd1-4d73ef9bc151)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/0b6dba2b-b4db-4385-8584-c184394ffc70)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/41823a49-d2cf-4e9d-a1c9-6997a5f8c932)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/e7a0e2ae-dcd9-47bc-a9e4-9d3db8f5d400)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/5e81259f-cedf-4939-a558-f56758ce5857)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/955d1882-986d-4988-ac84-5e8388eb07dd)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/6248d8de-8535-4877-b1aa-ce91a31583f4)


![image](https://github.com/Leela1822/DS_exp4/assets/106167639/5d169ac6-a47c-4aa8-bcdb-70b40d831653)




# RESULT:
Thus the program to perform EDA on the given data set is successfully executed.
