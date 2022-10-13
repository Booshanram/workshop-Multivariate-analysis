# workshop-Multivariate-analysis

Aim :
To perform Multivariate Exploratory Data Analysis in the given data set
Program Code :
import pandas as pd
import numpy as np
import seaborn as sbn
import matplotlib.pyplot as plt
df = pd.read_excel("/content/FlightInformation.xlsx")
df.head(10)
df.info()
df.describe()
df.isnull().sum()
df['Route'] = df['Route'].fillna(df['Route'].mode()[0])
df['Total_Stops'] = df['Total_Stops'].fillna(df['Total_Stops'].mode()[0])
df.isnull().sum()
df.dtypes
sbn.scatterplot(df['Airline'],df['Price'])
airline=df.loc[:,["Airline","Price"]]
airline=airline.groupby(by=["Airline"]).sum().sort_values(by="Price")
plt.figure(figsize=(17,7))
sbn.barplot(x=airline.index,y="Price",data=airline)
plt.xticks(rotation = 90)
plt.xlabel=("AIRLINE")
plt.ylabel=("PRICE")
plt.show()
sbn.barplot(x=df["Price"],y=df["Source"],data=df)
sbn.displot(df, x="Source", hue="Airline")
sbn.displot(df, x="Destination", hue="Airline")
sbn.countplot(df['Total_Stops'],hue=df['Additional_Info'])
sbn.pointplot(df['Source'],df['Price'],hue=df['Additional_Info'])
sbn.barplot(df['Source'],df['Price'],hue=df['Destination'])
sbn.barplot(df['Source'],df['Price'],hue=df['Additional_Info'])
df.corr()
sbn.heatmap(df.corr(),annot=True)
Output :
BIVARIATE ANALYSIS – NUMERICAL a
BIVARIATE ANALYSIS – CATEGORICAL AND CATEGORICAL
MULTIVARIATE ANALYSIS
