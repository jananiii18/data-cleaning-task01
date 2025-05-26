# data-cleaning-task01
Netflix Movies and Tv Shows Data Set Cleaning

#importing data set using pandas library
import pandas as pd
df = pd.read_csv("netflix_titles.csv")
df

#knowing the shape with null and duplicates value
df.shape

#checking null values
df.isnull()

#checking coloumn wise null values
df.isnull().sum()

#checking overall null values
df.isnull().sum().sum()

#filling null values with 0
df2 = df.fillna(value = 0)

#converting to date time format
df3['date_added'] = df3['date_added'].astype(str).str.strip()
df3['date_added'] = pd.to_datetime(df3['date_added'], errors='coerce')
df3['date_added'] = df3['date_added'].dt.strftime('%d/%m/%Y')

#removing null values if all the coloumn contains null value
df3 = df.dropna(how="all")

#removing null values if any one of the coloumn contains null value
df5 = df3.dropna(how="any")

#sorting acording to the type 
df6 = df5.sort_values(by='type', ascending=True)
df6 = df6.reset_index(drop=True)
print(df6[['type', 'title']])


#exported the cleaned data set
df6.to_csv(r'C:\Users\janan\OneDrive\Documents\m\data-cleaning-task1.csv', index=False) 
