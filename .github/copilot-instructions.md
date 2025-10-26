# AI Agent Instructions for Video Game Sales Analysis Project

## Project Overview
This is a data analysis project focused on analyzing video game sales data across different regions (NA, EU, JP, Other) using Python and Pandas. The project is structured as a Jupyter notebook-based analysis with specific focus on sales patterns and market differences.

## Key Components
- `vgsales.csv`: Primary dataset containing video game sales data
- `assignment.ipynb`: Main analysis notebook with structured questions and analysis
- `myenv.yml`: Conda environment configuration

## Data Structure
The video game sales dataset includes the following key columns:
- Name: Game title
- Platform: Gaming platform
- Year: Release year
- Genre: Game genre
- Publisher: Game publisher
- Regional Sales: NA_Sales, EU_Sales, JP_Sales, Other_Sales (in millions)
- Global_Sales: Total worldwide sales

## Common Analysis Patterns

### Data Loading and Initial Processing
```python
import numpy as np
import pandas as pd
df = pd.read_csv('vgsales.csv')
```

### Sales Analysis Patterns
1. Regional comparisons using boolean filtering:
```python
df[df['JP_Sales'] > df['NA_Sales']]  # Compare regional sales
```

2. Multi-metric aggregation:
```python
df.groupby('Publisher').agg(
    Name_count=('Name', 'nunique'),
    Sales=('Global_Sales', 'sum')
)
```

### Visualization Conventions
- Use standard pandas display for data frames
- Prefer simple, direct data presentation over complex visualizations

## Environment Setup
1. Use the provided conda environment:
   ```bash
   conda env create -f myenv.yml
   conda activate base
   ```

## Best Practices
1. Always create a copy when filtering data for analysis:
   ```python
   df_filtered = df[condition].copy()
   ```
2. Use descriptive variable names (e.g., `df_jp` for Japanese market analysis)
3. Include summary statistics before detailed analysis
4. Document insights in markdown cells between analysis sections

## Common Workflows
1. Regional market analysis:
   - Filter by region
   - Analyze by genre/publisher
   - Compare sales metrics
2. Temporal analysis:
   - Filter by year
   - Track trends across platforms/genres
3. Market share calculation:
   - Calculate percentages of total sales
   - Compare regional contributions