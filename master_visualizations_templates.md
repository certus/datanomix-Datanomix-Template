# Master Visualization Templates

This file contains links to the corporate templates of the different types of master visualization objects.

Use these templates as an example and a guideline to implement new master visualization objects.

## KPIs

### KPI with a relative growth indicator
Type: KPI
Name: Total Sales, USD
Description: Shows the measure in the current period and a growth/decline compared to the previous period in %.
File: 8f4f1704-fb34-426a-b24e-52863127f501.json
Features:
- YTD comparison with previous year
- Conditional coloring (green for growth, red for decline)
- Direction arrows (up/down) for visual indication
- Detailed tooltips with absolute values

### KPI with tooltip chart
Type: KPI
Name: Total Sales, USD (with chart tooltip)
Description: Similar to standard KPI but includes a mini chart in the tooltip showing weekly trends.
File: dc4b4b13-d94b-4463-ba6e-90ccc84d8536.json
Features:
- Same YTD comparison as standard KPI
- Includes mini area chart in tooltip showing weekly data
- Exponential trend line in tooltip chart

## Bar Charts

### Diverging bar
Type: Bar chart
Name: Diverging bar
Description: A simple standard bar chart that can handle both negative and positive magnitude values.
File: bd16629d-4539-4dc4-a794-ea24e3488f07.json
Features:
- Horizontal orientation
- Color based on profit margin (above/below midpoint)
- Data labels shown

### Ordered bar
Type: Bar chart
Name: Ordered bar
Description: Standard bar chart with items sorted by value to display ranks more easily.
File: 32fd7359-5058-4c81-90ba-5a0129ed4b07.json
Features:
- Horizontal orientation
- Items sorted by value
- Single color scheme
- Data labels shown
- Mini chart scrollbar

### Ordered bar with alternative dimensions and measures
Type: Bar chart
Name: Ordered bar with alternative dimensions and measures
Description: Advanced bar chart that allows switching between different dimensions and measures.
File: 5ab11669-fb6c-4862-a637-84cd6a93bf4c.json
Features:
- Alternate between "ProductName" and "Category" dimensions
- Horizontal orientation
- Items sorted by values
- Support for data-driven coloring
- Mini chart scrollbar for navigation

### Ordered bar with multiple measures
Type: Bar chart
Name: Ordered bar with multiple measures
Description: Bar chart that displays multiple measures for each dimension value.
File: e8b9aa3c-1079-4298-9dd6-98b6ff4e76e5.json
Features:
- Shows both Sales Amount and Gross Profit measures
- Horizontal orientation with items sorted by values
- Legend for multiple measures
- Mini chart scrollbar for navigation
- Data labels shown

## Line Charts

### Standard line chart
Type: Line chart
Name: Line
Description: The standard way to show a changing time series. Includes markers to represent data points.
File: 38ec576f-ab0c-4074-b710-c2770cc3a7b7.json
Features:
- Time series visualization (by month)
- Data points shown
- Custom line styling
- Suitable for showing trends over time

### Current vs Previous Period Comparison
Type: Line chart
Name: Actual vs Previous Period Measure Comparison
Description: Display one time dimension (year, quarter, month, week) and two measures: for current period and for previous period.
File: c624e42b-9730-4cdb-854f-e1d5d60d5337.json
Features:
- Monthly time dimension by default
- Compares current YTD data with previous year YTD data 
- Standardized color scheme (current period in brand color, previous period in gray)
- Data points shown for better readability
- Ideal for YoY performance tracking

### Area chart for tooltips
Type: Line chart (Area)
Name: Total Sales
Description: A minimalist area chart designed for displaying in tooltips.
File: e0723c48-7c64-4e3c-b47a-1ddfb098dc70.json
Features:
- Weekly time dimension
- No axis labels or grid lines
- Exponential trend line
- Designed for compact display in tooltips

## Measures

### Total Sales
ID: PXKaj
Description: Sum of sales amount for the current year to date.
Features:
- YTD calculation using date ranges
- Used in KPI visualizations with YoY comparisons

### Profit Margin
ID: Jmpyv
Description: Average gross profit margin (centered at 0.5 for diverging coloring).
Features:
- Used for conditional coloring in diverging bar charts
- Formatted as percentage

### Gross Profit
ID: 5cdae00d-5288-4dac-aa3c-a626a7414850
Description: Sum of gross profit for the current year to date.
Features:
- YTD calculation using date ranges
- Used as a secondary measure in multi-measure visualizations

### Sales LYTD
ID: qFPJJCm
Description: Sum of sales amount for the last year to date (for comparison).
Features:
- Always displayed in gray color for consistency
- Used in current vs previous period comparisons
- Same date range as current period but shifted back one year