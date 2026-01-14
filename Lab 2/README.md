# The Illusion of Growth & The Composition Effect

## Objective

This project builds a Python-based analytical pipeline to investigate wage stagnation and statistical biases in labor market data using live Federal Reserve Economic Data (FRED). By connecting directly to the St. Louis Fed's API, I demonstrate how nominal wage growth masks purchasing power stagnation and how composition effects can create misleading signals during economic shocks.

## Methodology

### Data Acquisition & Processing
- **API Integration**: Implemented `fredapi` to programmatically fetch time-series data from the Federal Reserve's database
- **Primary Series**:
  - `AHETPI`: Average Hourly Earnings of Production and Nonsupervisory Employees
  - `CPIAUCSL`: Consumer Price Index for All Urban Consumers
  - `ECIWAG`: Employment Cost Index for Total Compensation

### Analytical Framework

**1. Real Wage Calculation**
- Constructed inflation-adjusted wage series using CPI deflation
- Formula: `Real Wage = (Nominal Wage / CPI_t) × CPI_current`
- Time span: 1964-Present (60+ years of labor market history)

**2. Composition Bias Detection**
- Identified anomalous spike in real wages during Q2 2020
- Hypothesis: The "pandemic wage boom" reflects sample composition changes, not true wage increases
- Workers who lost jobs during COVID-19 lockdowns were disproportionately lower-wage service workers, artificially inflating the average

**3. Bias Correction Using ECI**
- Fetched Employment Cost Index (ECI), which holds occupation and industry mix constant
- Rebased both series to 100 (2015 baseline) for direct comparison
- Demonstrated that ECI shows stable growth while standard average wages show artificial volatility

### Technical Implementation
- **Languages & Libraries**: Python, pandas, matplotlib, seaborn
- **Visualization**: Created publication-quality time-series plots with annotated economic events
- **Statistical Methods**: Index rebasing, CPI deflation, comparative time-series analysis

## Key Findings

### The Money Illusion
Over the past 60 years, nominal wages have increased dramatically from $2.50/hour to $31.76/hour—a 12x increase. However, when adjusted for inflation, real purchasing power has grown only modestly, rising from approximately $26.35 to $31.76 in 2025 dollars. This "money illusion" obscures the reality of wage stagnation for production workers.

### The Pandemic Paradox
The 2020 COVID-19 pandemic created a striking statistical artifact in wage data:

- **Standard Average Wages** surged by 20.87% from 2015 to Q2 2020
- **Employment Cost Index** rose by only 14.85% over the same period
- **Composition Bias**: 6.02 index points of the apparent wage growth was attributable to low-wage workers exiting the labor force

This 6-point divergence represents the **composition effect**—not genuine wage increases, but a statistical mirage created by changing workforce demographics. When service sector workers (restaurant staff, retail workers, hotel employees) were laid off en masse, the remaining workforce was disproportionately higher-paid, mechanically inflating the average.

The ECI, which controls for occupation and industry mix, reveals the truth: wage growth remained steady and modest throughout the pandemic. There was no "wage boom"—only a compositional shift that created the illusion of one.

### Economic Implications
This analysis demonstrates why policymakers must use composition-adjusted metrics like the ECI rather than simple averages when evaluating labor market health. The 2020 divergence serves as a cautionary tale about interpreting aggregate statistics during periods of economic disruption.

---

**Technical Skills Demonstrated**: API integration, time-series analysis, econometric bias correction, data visualization, economic interpretation

**Data Source**: Federal Reserve Economic Data (FRED), Federal Reserve Bank of St. Louis
