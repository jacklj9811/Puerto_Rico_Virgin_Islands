# Puerto Rico Virgin Islands

It is GIS data. Here's a step-by-step guide to set up a simple Python project using the data:
## Part 1: Step by step tutorial on Exploratory Data Analysis(EDA)

### Step 1: Set Up Your Project Environment

1. **Create a Project Directory**: Organize your project files in a dedicated folder.

a. If you have installed conda, you can just use the following command in Anaconda Prompt:
```bash
conda env create -f environment.yml
```

b. If you do not have installed conda, please follow step b.1 to b.2.

b.1. **Initialize a Python Environment**: 

 use virtual environments (`venv`) to manage your project dependencies.
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

b.2. **Install Required Libraries**: Install `geopandas` for GIS data manipulation, and `matplotlib` or `folium` for visualization.

```bash
pip install geopandas matplotlib folium
```

### Step 2: Load and Clean the Data

1. **Load the Data**: Use `geopandas` to read the shapefile(s).

```python
import geopandas as gpd

# Adjust the file path as needed
data_path = 'LF2023_PRVI_240_IA/LF2023_LDist_240_PRVI/Spatial_Metadata/z90_prvi_0k.shp'
gdf = gpd.read_file(data_path)
```

2. **Clean the Data**: Perform any necessary data cleaning steps, such as removing missing values or filtering the data.

```python
# Example: Remove features with missing geometry
gdf = gdf[gdf.geometry.notnull()]
```

### Step 3: Analyze the Data

1. **Perform Spatial Analysis**: Depending on your project goal, this might include calculating areas, distances, spatial joins, or other GIS operations.

```python
# Example: Calculate the area of each feature
gdf['area'] = gdf.geometry.area
```

### Step 4: Visualize the Data

1. **Create Visualizations**: Use `matplotlib` for static maps or `folium` for interactive maps.

```python
import matplotlib.pyplot as plt

gdf.plot(column='area')
plt.show()
```

Or for an interactive map:

```python
import folium

m = folium.Map(location=[latitude, longitude], zoom_start=12)
folium.GeoJson(gdf).add_to(m)
m.save('map.html')
```

## Part 2: Basic Data Analysis

### 1. Data Loading and Cleaning
```python
import pandas as pd

# Load a dataset
df = pd.read_csv('LF2023_PRVI_240_IA/LF2023_LDist_240_PRVI/CSV_Data/dataset.csv')

# Display the first few rows
print(df.head())

# Clean the data
df.dropna(inplace=True)  # Remove missing values
df = df[df['column_name'] > 0]  # Filter based on a condition
```

### 2. Data Visualization
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Basic plot
plt.plot(df['x_column'], df['y_column'])
plt.xlabel('X Axis Label')
plt.ylabel('Y Axis Label')
plt.title('Basic Plot')
plt.show()

# Advanced visualization with seaborn
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.title('Heatmap of Correlation Matrix')
```

### 3. Basic Statistical Analysis
```python
from scipy import stats

# Descriptive statistics
print(df.describe())

# T-test example
t_stat, p_val = stats.ttest_ind(df['group1'], df['group2'])
print(f'T-statistic: {t_stat}, P-value: {p_val}')
```

### 4. Machine Learning Model Example
```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

# Split the data
X_train, X_test, y_train, y_test = train_test_split(df.drop('target_column', axis=1), df['target_column'], test_size=0.2, random_state=42)

# Initialize and train a model
model = RandomForestClassifier()
model.fit(X_train, y_train)

# Make predictions and evaluate the model
predictions = model.predict(X_test)
print(f'Model Accuracy: {accuracy_score(y_test, predictions)}')
```

### 5. Working with Geospatial Data
```python
import geopandas as gpd

# Load a shapefile
gdf = gpd.read_file('path/to/your/shapefile.shp')

# Plot the geospatial data
gdf.plot()
plt.show()
```
