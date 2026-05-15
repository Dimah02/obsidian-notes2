>You can work with series and data frames
- A series is like one dimensional label column
- A Data Frame is like two dimensional labeled grid or table
with this library you can Import, Display, Manipulate and Export tabular data

# Series 
```python
import numpy as np
import pandas as pd

# Series = A pandas 1-dimentsional labeled array that canhold any data type
#  Think of it like a single column in a spreadsheet 

data = [100,102,104]

# Converst an array to a series by calling the series conustructor
# It create a defualt index and shows the data type of the data
series = pd.Series(data)
print(series)

data = [100.1,102.2,104]
series = pd.Series(data)
print(series)

data = ['A','B','C']
series = pd.Series(data)
print(series)

data = [True ,False]
series = pd.Series(data)
print(series)

# To provide a custome index
data = [100,102,104,200,202]
series = pd.Series(data, index = ["a","b","c","d","e"])
print(series)

# To Access a value in a series

series.loc["c"] = 200
print(series.loc["c"])

# Can locate by integer position
print(series.iloc[0])

# Filter by value
# return any value with >= 200
print(series[series>=200])

# Using dectionary
calories = {
	"Day 1": 1750,
	"Day 2":2100,
	"Day 3":1700
}
series = pd.Series(calories)
# Keys will be the index
print(series)
print(series.loc["Day 1"])

print(series[series>=2000])
```

# Data Frame
```python
import pandas as pd

# DataFrame = A tabular data structure wiith rows and columns 
# similar to an excel spreadsheet

data = {
	"Name":["Dima", "Sara", "Nadia"],
	"Age": [30,35,50]
}

df = pd.DataFrame(data, index = ["1","2","3"])

print(df)

# Select a specific row 
print(df.loc["1"])

# Add a new Column
df["Job"] = ["Chef", "Acountant", "Dev"]

print(df)

# Add a new Row

new_row = pd.DataFrame([{"Name":"Sandy","Age":28,"Job":"Engineer"}],
	index = ["4"])

df = pd.concat([df,new_row])

print(df)

# Add new Rows
new_rows = pd.DataFrame([{"Name":"Sama","Age":33,"Job":"Engineer"},{"Name":"Dana","Age":15,"Job":"Manager"}],
	index = ["5","6"])

df = pd.concat([df,new_rows])

print(df)
```

# Importing
```python
import pandas as pd

df = pd.read_csv("ultimate_student_productivity_dataset_5000.csv")

print(df)

# to print all the data print(df.to_string())

df = pd.read_csv("pocimon.csv")

print(df.to_string())

# pd.read_json("data.json")
```

# Selection
```python
import pandas as pd


df = pd.read_csv("pocimon.csv")

# Selection By Column
print(df["Name"])

# defualt print print only the first and last 5 columns 
# if you want to print all data use to_string()

print(df["Weight"].to_string())


# To print sub features
print(df[["Name", "Height"]].to_string())

#Selection by rows
print(df.loc[1])


# Can change the index to be the names for the pocimon
df = pd.read_csv("pocimon.csv", index_col="Name")
print(df.loc["Pikachu"])

# Can select features to print
print(df.loc["Charizard", ["Height", "Weight"]])

# To select a range of rows
print(df.loc["Charizard":"Blastoise", "Weight"])

# Use integer based indexing 
#           first 5 even rows , first 3 columns
print(df.iloc[0:11:2, 0:3])

#pokemon = input("Enter a Pokemon name:")
#try:
#	print(df.loc[pokemon])
#except KeyError:
#	print(f"{pokemon} not found")
```
# Filtering
```python
import pandas as pd
df = pd.read_csv("pocimon.csv")

# Filtering = keeping the rows that match a condition

# filter by height

tall_pokemon = df[df["Height"] >= 2]
print(tall_pokemon)

legendary_pokemon = df[df["Legendary"]==True]

print(legendary_pokemon)

# If you are using the logical operator enclose your condition with ()
water_pokemon = df[(df["Type1"]=="Water") | (df["Type2"] == "Water")]
print(water_pokemon)
```
# Aggregation
```python
import pandas as pd

df = pd.read_csv("pocimon.csv")

# Whole dataframe
print(df.mean(numeric_only=True))
print(df.sum(numeric_only=True))
print(df.min(numeric_only=True))
print(df.max(numeric_only=True))

# Counting the number of values in each column and it will not include any null value
print(df.count())

# Single Column
print(df["Height"].mean())
print(df["Height"].sum())
print(df["Height"].min())
print(df["Height"].max())
print(df["Height"].count())

# Group by
group = df.groupby("Type1")

print(group["Height"].mean())
print(group["Height"].sum())
print(group["Height"].count())
```

# Data Cleaning
```python
import pandas as pd


df = pd.read_csv("pocimon.csv")

# Data cleaning = the process of fixing/removing:
#				  incomplete, incorrecct or irrelevent data.



# To drop a column

df = df.drop(columns = ["Legendary","No"])


# To handel Missing data
# Drop not available
# Will drop any rows that contain a missing value
#df = df.dropna(subset = ["Type2"])


# To replace null values
# Fill any not availabe row
df = df.fillna({"Type2": "None"})

# Fix incosistent value
# replace any word Grass in type1 column with GRASS
df["Type1"] = df["Type1"].replace({"Grass":"GRASS", "Fire":"FIRE"})


# Standardize text
df["Name"] = df["Name"].str.lower()

# Fix data type
df = pd.read_csv("pocimon.csv")

df["Legendary"] = df["Legendary"].astype(bool)


# Remove duplicate values
df = df.drop_duplicates()
print(df.to_string())
```
