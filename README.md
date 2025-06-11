# COVID‑19 Analysis & Visualization with Plotly Express

## 🚀 Project Overview
This project explores COVID‑19 data using **Plotly Express** to create interactive and animated visualizations. It provides insights into trends and geographic spread of the pandemic.

### 🔍 Key Takeaways
- **Interactive charts**: Line, bar, scatter, bubble plots, and choropleth maps.
- **Animations**: Time-series transitions (e.g., cases over time by country).
- **Geographic analysis**: Animated world maps and choropleth visualizations.
- **Statistical visuals**: Histograms, box plots, density contours.

## 📁 Repository Structure
- `covid_analysis_plotly.ipynb` – Jupyter Notebook with full analysis and charts.
- `README.md` – Project overview and instructions.
- `requirements.txt` – List of dependencies.
- `data/` – (Optional) COVID‑19 datasets (e.g., from Johns Hopkins or Worldometer).

## 🧰 Tools & Technologies
- **Python 3**
- **Plotly Express** – interactive visualizations :contentReference[oaicite:2]{index=2}
- **Pandas** – data manipulation :contentReference[oaicite:3]{index=3}
- **NumPy** (as needed)

## 📝 Typical Analysis Steps
# 1. Import Libraries
import pandas as pd
import plotly.express as px
import plotly.figure_factory as ff

# 2. Load Dataset
dataset1 = pd.read_csv('covid_19_data.csv')

# 3. Clean and Inspect Data
dataset1.fillna(0, inplace=True)
dataset1.head()
dataset1.info()

# 4. Top 10 Countries by Total Cases
top_10 = dataset1.sort_values(by='TotalCases', ascending=False).head(10)

# 5. Bar Plot - Top 10 Countries
px.bar(top_10, x='Country/Region', y='TotalCases', color='Country/Region')

# 6. Pie Chart - Top 15 by Deaths
px.pie(dataset1.head(15), values='TotalDeaths', names='Country/Region')

# 7. Scatter Plot - Tests vs GDP
px.scatter(dataset1, x='GDP/Capita', y='Tests/1M pop',
           size='Population', color='Continent',
           hover_name='Country/Region', size_max=60)

# 8. Bubble Plot - Population vs Cases
px.scatter(dataset1, x='TotalCases', y='Population',
           size='Tests/1M pop', color='Continent')

# 9. Choropleth Map - Confirmed Cases
px.choropleth(dataset1,
              locations='Country/Region',
              locationmode='country names',
              color='TotalCases',
              hover_name='Country/Region',
              color_continuous_scale='Viridis')

# 10. Optional Table Display
table = ff.create_table(dataset1.head(15))
table.show()


