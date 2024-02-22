# Puerto Rico Virgin Islands
## Step by step tutorial:
It is GIS data. Here's a step-by-step guide to set up a simple Python project using the data:

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

```bash
git init
git add .
git commit -m "Initial project setup with GIS analysis"
git remote add origin <your-repository-url>
git push -u origin master
```
