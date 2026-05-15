# Basic plots
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

x = np.array([2023, 2024, 2025, 2026])
y = np.array([15, 25, 30, 20])

# x-axis and y-axis
plt.plot(x,y)

plt.show()
```

# Plot Customization
```python
import numpy as np
import matplotlib.pyplot as plt

x = np.array([2023, 2024, 2025, 2026])
y = np.array([15, 25, 30, 20])

# . coordinates will be a point\
# o for circle
# v for traingle down
# * for star
# you can search for matplotlib.markers for more

plt.plot(x,y, marker = "*",
	markersize=10, # shorter ms
	markerfacecolor="#1cd3fc", #shorter mfc
	markeredgecolor="#1cd3fc", # mec
	linestyle="dashed", # default = solid, dotted, dashdot, None
	linewidth=4,
	color="#1c5bfc"
	) 

plt.show()
```
### Multiple lines
```python
import numpy as np
import matplotlib.pyplot as plt

x = np.array([2023, 2024, 2025, 2026])
y1 = np.array([15, 25, 30, 20])
y2 = np.array([17, 23, 38, 5])
y3 = np.array([13, 15, 20, 30])

line_style = dict(
	marker = "*",
	markersize=10, # shorter ms
	markerfacecolor="#1cd3fc", #shorter mfc
	markeredgecolor="#1cd3fc", # mec
	linestyle="dashed", # default = solid, dotted, dashdot, None
	linewidth=4,
	
	)

plt.plot(x,y1,color="#1c5bfc",**line_style) 

plt.plot(x,y2,color="#1cfc45", **line_style)

plt.plot(x,y3,color="#fc1c1c", **line_style)


plt.show()
```
# Adding Labels
```python
import numpy as np
import matplotlib.pyplot as plt

x = np.array([2023, 2024, 2025, 2026])
y1 = np.array([15, 25, 30, 20])
y2 = np.array([17, 23, 38, 5])
y3 = np.array([13, 15, 20, 30])

plt.title("Class size",
 fontsize=20,
 family="Arial",
 fontweight="bold",
 color ="purple")

plt.xlabel("Year")

plt.ylabel("Students")

# Force x to display the data values only
plt.xticks(x)

plt.tick_params(axis="both",
	colors="cyan")

plt.plot(x,y1) 

plt.plot(x,y2)

plt.plot(x,y3)

plt.show()
```

# Grid lines
```python
import numpy as np
import matplotlib.pyplot as plt

# gird() = Helps make plots easier to read by adding reference lines.

x = [ 1,2,3,4,5]

y = [5,10,15,20,25]

# plt.grid() will show grid on both x and y axis

# will show only grid on the x axis
plt.grid(axis="x")

# will show only grid on the y axis
plt.grid(axis="y", linewidth=2,color="lightgray", linestyle="dashed")


plt.plot(x,y)

plt.show()
```

# Bar charts
```python
import numpy as np
import matplotlib.pyplot as plt

# Bar chart = compare categories of data by representing each category with a bar

categories = np.array(["Grains", "Fruit", "Vegetables", "Protein", "Dairy", "Sweets"])

values = np.array([4,3,2,5,3,1])


 plt.bar(categories,values, color="Green")

# For a horizontal bar chart
#plt.barh(categories,values, color="Green")

plt.title("Daily consumption")
plt.xlabel("Food")
plt.ylabel("Count")

plt.show()
```

# Pie chart
```python
import numpy as np
import matplotlib.pyplot as plt

# Pie chart = Circular chat divided into slices to show percentages of total
categories = np.array(["Grains", "Fruit", "Vegetables", "Protein", "Dairy", "Sweets"])

values = np.array([4,3,2,5,3,1])

colors = ["red","green","yellow","blue","purple","cyan"]

plt.pie(values,
	labels=categories,
	autopct="%1.1f%%",
	colors=colors,
	explode=[0,0,0,0.1,0,0],
	shadow=True,
	startangle=90
	)

plt.title("IDK")
plt.show()
```



# Scatter graph
```python
import numpy as np
import matplotlib.pyplot as plt

# Scatter graph = shows the relationship between two variables 
# Help to identify a coreelation (+ , - , None)
# Example: study hours vs Test scores

x1 = np.array([0, 1, 1, 2 , 3, 4 , 5 , 6 , 7 , 7, 8 , 9, 10 ,11 ,15] )# Hours studied
y1 = np.array([55,60,65,62,68,70,75,78,82,85,87,90,93,94,95]) # Grades


x2 = np.array([0, 2, 2, 3 , 4, 5 , 7 , 7 , 7 , 7, 8 , 9, 10 ,11 ,13] )# Hours studied
y2 = np.array([50,65,65,68,69,71,76,79,85,86,87,90,96,97,98]) # Grades

plt.scatter(x1,y1,
	color="skyblue",
	alpha=0.5,
	s = 200, # for size
	label="Class A",
	)

plt.scatter(x2,y2,
	color="red",
	alpha=0.5,
	s = 200, # for size
	label="Class B",
	)

plt.xlabel("Hours Studied")

plt.ylabel("Grade")

plt.title("Test Scores")

plt.legend()
plt.show()
```
# Histogram
```python
import numpy as np
import matplotlib.pyplot as plt

# Histogram : A viual representaion of the distribution of quantitative data.
# They group values into bins (intervals)
# and counts how many fall in each range

x1 = np.array([0, 1, 1, 2 , 3, 4 , 5 , 6 , 7 , 7, 8 , 9, 10 ,11 ,15] )# Hours studied
y1 = np.array([55,60,65,62,68,70,75,78,82,85,87,90,93,94,95]) # Grades

# To generate random array with normal distibution with center = loc and scale = standart divitaion, size how many number you want to genrerate
scors = np.random.normal(loc=80,scale=10,size=100)

# to make sure that scores are between 0 and 100 use clip
scors = np.clip(scors, 0,100)

plt.hist(scors,
	bins = 10,
	color="purple",
	edgecolor="white",
	)

plt.title("Exam Scores")

plt.xlabel("score")
plt.ylabel("Number of studets")
plt.show()
```

# Subplots
```python
import numpy as np
import matplotlib.pyplot as plt

# Figure = the entire canvas 
# Ax = A singlle plot (subplot)


figure, axes = plt.subplots(2,2)

x = np.array([1,2,3,4,5])

axes[0,0].plot(x,x*2, color="Green")
axes[0,0].set_title("x * 2")


axes[0,1].plot(x,x**2,color="purple")
axes[0,1].set_title("x ** 2")

axes[1,0].plot(x,x**3,color="cyan")
axes[1,0].set_title("x ** 3")

axes[1,1].plot(x,x**4,color="red")
axes[1,1].set_title("x ** 4")

plt.tight_layout()

plt.show()
```


# Matplotlib + pandas
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("data.csv")

type_count = df["Type1"].value_counts(ascending =True)

plt.barh(type_count.index,type_count.values)

plt.show()
```
