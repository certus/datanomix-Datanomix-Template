# Master Visualization Templates

This file contains links to the corporate templates of the different types of master visualization objects.

Use these templates as an example and a guideline to implement new master visualization objects.

## KPIs

### Common KPI Rules

#### Title Area
- **Title**:
  - Keep clear and concise (e.g., "Total Sales")
  - Include units of measure (e.g., "USD")
  - Avoid unnecessary text that clutters the display

- **Subtitle**:
  - Specify timeframes for both KPIs (e.g., "2024 YTD vs 2023 YTD")
  - Use dynamic expressions: `='$(=Max(Year)) YTD vs $(=Max(Year)-1) YTD'`
  - Ensure subtitle complements the title without redundancy

- **Footnote**:
  - Display data currency with timestamp: `='Last data: $(=Date(Max(TransactionDate)))'`
  - Use consistent date formatting across all KPI objects

#### Primary KPI (First Measure)
- Label for the first KPI = object title.
- Use appropriate number formatting based on measure type
- Use auto formatting

#### Secondary KPI (Second Measure)
- Include title that specifies comparison (e.g., "vs LYTD")
- Format as percentage with one decimal place and Place +/- prefix before the value: (`+#,##0.0%;-#,##0.0%` for MoneyDecimalSep='.', and `+# ##0,0%;-# ##0,0%` for MoneyDecimalSep=',')
- Configure conditional colors:
  - Set limit expression to 0 (zero)
  - Growth (>0): Use colorblind-safe green (#38A169)
  - Decline (<0): Use colorblind-safe red (#E53E3E)
- Configure symbols:
  - Growth (>0): Use upward arrow (▲)
  - Decline (<0): Use downward arrow (▼)

#### Link Trend Chart Master Visualization to KPI Tooltip
- Add "chart" property to the "tooltip" section of the KPI's json, using the following JSON template.
- object.refId = {GUID} of the added Master Visualization Trend Chart.
- refId should always be a GUID.
- Read and follow instructions in comments /* INSTRUCTION: */ in the JSON template.
```json
"tooltip": {
          "chart": {
            "style": {
              "size": "medium"
            },
            "object": {
              "refId": "e0723c48-7c64-4e3c-b47a-1ddfb098dc70"
            }
          }
}
```

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