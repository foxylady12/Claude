# Junior Miner Select - Investment Analysis Framework

## Overview

This analysis framework evaluates junior mining companies using a comprehensive, data-driven scoring methodology. It processes financial and operational metrics to identify investment opportunities across different risk-reward profiles.

**Key Output**: A ranked list of junior mining companies with scores, tiers, and cluster classifications to support investment decision-making.

---

## What The Analysis Does

### 1. Data Quality Screening

Before analysis begins, companies are filtered through two quality screens:

- **Missing Data Screen**: Companies lacking critical financial metrics (market cap, debt ratios, cash flow, etc.) are excluded and placed in a "Data Catcher" sheet for reference.

- **Collapsed Market Cap Screen**: Companies whose current market cap has fallen below 75% of their 3-year average are flagged. This identifies potential distressed situations that require separate evaluation.

**Result**: Only companies with complete, reliable data proceed to scoring.

---

## The Scoring Methodology

### Core Philosophy

The framework evaluates companies across **7 fundamental factors**, each measuring a specific aspect of investment quality. All metrics are standardized so that **higher scores always indicate better performance**.

### The 7 Investment Factors

#### 1. **Survival Factor**
*"Can this company continue operating?"*

Measures the company's ability to sustain operations without additional financing:

- **Burn in Months**: How long can the company operate at current cash burn rate? (Higher = better)
- **Net Debt / Market Cap**: Debt burden relative to company value (Lower debt = better; score inverted)
- **Cash-to-Capex Coverage**: Can the company fund capital expenditures from existing cash?

**Scoring**: "Burn in Months" uses custom logic:
- Companies with positive cash generation = Score of 5
- Companies burning cash = Scored 1-4 based on runway length (shorter runway = lower score)

#### 2. **Investment Quality Factor**
*"Is the company efficiently deploying capital?"*

Evaluates how well the company invests in productive assets:

- **CapEx / Market Cap (3Y Average)**: Capital investment intensity relative to company size
- **Head Office Efficiency**: Administrative costs relative to operations (Lower overhead = better; score inverted)

**Interpretation**: Higher scores indicate companies that invest heavily in their projects while maintaining lean operations.

#### 3. **Financial Stability Factor**
*"Is the company generating real cash flow?"*

Measures operational cash generation and balance sheet health:

- **Cash from Operations / Market Cap**: Operating cash flow yield
- **Net Debt / Market Cap**: Financial leverage (also used in Survival factor)

**Interpretation**: Higher scores indicate companies generating positive cash from their core business.

#### 4. **Shareholder Friendliness Factor**
*"Are shareholders being treated well?"*

Tracks dilution and capital structure decisions:

- **Share Count Change (1Y)**: Change in shares outstanding (Lower dilution = better; score inverted)

**Interpretation**: Higher scores indicate companies financing growth without heavily diluting existing shareholders.

#### 5. **Valuation Factor**
*"Is the stock trading at an attractive price?"*

Assesses relative valuation:

- **Price-to-Book Ratio**: Market value vs. book value (Lower P/B = better value; score inverted)

**Special Feature**: Companies are first categorized by operational stage (Explorer/Developer/Producer) based on cash flow generation. P/B ratios are then scored **within each stage group**, ensuring fair comparisons between companies at similar development stages.

#### 6. **Market Momentum Factor**
*"What is the market telling us?"*

Captures recent price performance:

- **Total Return (1Y)**: Stock price performance over the past year

**Interpretation**: Higher scores indicate positive market sentiment and momentum.

#### 7. **Real Growth Factor**
*"Is the company actually growing?"*

Measures tangible asset and investment growth:

- **Net PP&E CAGR (3Y)**: Property, plant, and equipment growth rate
- **Total Assets CAGR (3Y)**: Overall asset base growth
- **CapEx CAGR (3Y)**: Capital expenditure growth trend

**Interpretation**: Higher scores indicate companies expanding their asset base and increasing investment levels (not just financial engineering).

---

## How Scoring Works

### Step 1: Individual KPI Scores (1-5 Scale)

For each metric within a factor:
- Companies are divided into **5 quintiles** (quintile ranking)
- Best quintile receives **Score of 5**
- Worst quintile receives **Score of 1**
- Middle groups receive 2, 3, or 4

**Example**: If analyzing "Cash from Operations / Market Cap":
- Top 20% of companies → Score 5
- Next 20% → Score 4
- Middle 20% → Score 3
- Next 20% → Score 2
- Bottom 20% → Score 1

### Step 2: Factor Scores (0-1 Normalized Scale)

Each factor's score is calculated by:
1. Summing the individual KPI scores within that factor
2. Normalizing to a 0-1 scale

**Formula**: `(Actual Sum - Minimum Possible) / (Maximum Possible - Minimum Possible)`

**Example**: Investment Quality has 2 KPIs:
- Minimum possible raw score: 2 (both KPIs score 1)
- Maximum possible raw score: 10 (both KPIs score 5)
- If a company scores 7: `(7-2)/(10-2) = 5/8 = 0.625`

**Result**: All factor scores range from 0.0 (worst) to 1.0 (best), allowing fair comparison across factors.

### Step 3: Total Scores (Two Methods)

#### **Additive Score** (Primary Ranking Method)
- Simply adds all 7 factor scores together
- Range: 0 to 7
- **Interpretation**: Measures overall quality across all dimensions
- **Use Case**: Identifies well-rounded companies with balanced strengths

#### **Multiplicative Score** (Alternative Ranking Method)
- Multiplies all 7 factor scores together
- Range: 0 to 1
- **Interpretation**: Penalizes significant weaknesses more heavily
- **Use Case**: Identifies companies that must be strong across ALL factors (no fatal flaws)

**Example Comparison**:
- Company A: All factors = 0.70 → Additive = 4.9, Multiplicative = 0.082
- Company B: Six factors = 0.80, one factor = 0.20 → Additive = 5.0, Multiplicative = 0.005

Company B ranks higher additively but much lower multiplicatively due to its one weak factor.

---

## Investment Tiers

Companies are classified into 3 investment tiers based on their **Additive Rank**:

### Tier 1: Investigate (Top 20%)
**Action**: Conduct detailed due diligence

These are the highest-scoring companies across the 7 factors. They represent the best risk-adjusted opportunities in the universe and warrant deep-dive analysis.

### Tier 2: Monitor (Next 40%, ranks 21-60%)
**Action**: Watch for entry points

Solid companies that may not currently be top-tier but could become attractive with:
- Improved fundamentals
- Better valuations
- Market dislocation creating opportunities

### Tier 3: Caution (Bottom 40%)
**Action**: Avoid or require special circumstances

Companies with significant weaknesses across multiple factors. Only consider if:
- You have specific catalysts or insider information
- You're pursuing a deep-value turnaround strategy
- Special situations justify the risk

---

## Company Clustering (Behavioral Profiles)

Beyond scoring, the analysis uses **K-means clustering** to group companies by behavioral characteristics. This identifies distinct "types" of junior miners:

### The 3 Cluster Profiles

#### **1. Speculative Growers**
**Characteristics**:
- Highest scores in Real Growth Factor
- Rapidly expanding asset base and capital spending
- Often earlier-stage companies

**Investment Profile**: High risk/high reward. These companies are aggressively building projects but may need ongoing financing.

#### **2. Stalwart Survivors**
**Characteristics**:
- Highest Financial Stability scores
- Strong cash generation from operations
- Conservative balance sheets

**Investment Profile**: Lower risk, steady performers. These companies can weather downturns and fund themselves internally.

#### **3. Investing Survivors**
**Characteristics**:
- Balanced Investment Quality and Survival metrics
- Moderate growth with decent financial position
- Not the strongest in any single dimension

**Investment Profile**: Middle ground. Reasonable risk-reward with ongoing capital deployment.

### How Clustering Helps

- **Peer Comparison**: Compare companies within their cluster (apples-to-apples)
- **Portfolio Construction**: Balance your portfolio across different behavioral profiles
- **Risk Management**: Understand what "type" of risk you're taking on

**Technical Note**: Clustering uses Principal Component Analysis (PCA) to visualize how companies group together based on all 7 factors simultaneously.

---

## Output Files Explained

### Excel Workbook Sheets

1. **Overview**: Summary statistics and analysis metadata
2. **Full Scoring & Clusters**: Complete ranked list with all scores (PRIMARY SHEET)
   - Filterable by "Selection_Status" to compare against a reference portfolio
3. **Cluster Profiles**: Average factor scores for each behavioral cluster
4. **Individual Cluster Sheets**: Top 50 companies in each cluster
5. **Tier Sheets**: Companies grouped by Tier 1/2/3 classification
6. **Tier Profile Analysis**: Statistical profiles (25th/50th/75th percentiles) for each tier
7. **Cluster Profile Analysis**: Statistical profiles for each behavioral cluster
8. **Tier-Cluster 3M Returns**: Performance analysis combining both classification systems
9. **Data Catcher**: Companies excluded for missing data
10. **Collapsed Mkt Cap Flag**: Companies flagged for distressed market caps

### PCA Scatter Plot (PNG)

Visual representation showing how companies cluster in 2-dimensional space based on their 7 factor scores. Companies close together in the plot have similar investment profiles.

---

## How to Use This Analysis

### For Portfolio Construction

1. **Start with Tier 1 companies** - These are your highest-probability opportunities
2. **Select across different clusters** - Diversify by company behavioral type
3. **Check the multiplicative rank** - Avoid companies with "fatal flaw" factors
4. **Review factor scores** - Understand each company's specific strengths/weaknesses

### For Due Diligence

1. **Compare factor scores to peers** - Use cluster assignments for relevant comparisons
2. **Investigate outliers** - Companies with extreme scores (very high or low) in specific factors
3. **Track changes over time** - Re-run analysis quarterly to monitor score trends
4. **Validate assumptions** - Scores are only as good as the underlying data

### For Risk Management

- **Survival Factor < 0.3**: Significant going-concern risk
- **Financial Stability Factor < 0.3**: Needs external financing soon
- **Shareholder Friendliness < 0.3**: Heavy dilution likely
- **Collapsed Market Cap Flag**: Investigate what caused the decline

---

## Important Limitations & Disclaimers

### Data Dependencies
- **Garbage in, garbage out**: Scores rely entirely on input data quality
- Missing or incorrect data can significantly skew rankings
- Historical data may not predict future performance

### Methodology Limitations
- **Equal factor weighting**: All 7 factors contribute equally to the additive score. Your investment strategy may prioritize some factors over others.
- **Quintile sensitivity**: Small changes in metrics can cause score changes when near quintile boundaries
- **No forward-looking data**: Scores are based on historical and current metrics, not projections
- **Sector-agnostic**: Doesn't account for commodity type (gold vs. lithium vs. copper, etc.)

### Not Investment Advice
This is a screening and ranking tool, not a recommendation system. It should be **one input** among many in your investment process:
- Conduct independent due diligence
- Consider qualitative factors (management, jurisdiction, geology, etc.)
- Assess macro conditions and commodity cycles
- Consult with licensed financial advisors

### Recommended Use
- **Screening tool**: Narrow the universe to companies worth deeper research
- **Comparative analysis**: Understand relative positioning
- **Change detection**: Track improving/deteriorating fundamentals
- **Portfolio monitoring**: Regular review of holdings' scores

---

## Technical Requirements

### Input Files Required

1. **Primary Dataset**: `koyfin_Junior Miners.csv`
   - Must contain all required KPI columns
   - ISIN or Ticker for company identification

2. **Optional Comparison Set**: `koyfin_Select Miners.csv`
   - Companies marked as "SELECT" for comparison filtering
   - Matched by ISIN (preferred) or Ticker

### Critical KPI Columns
- Market Cap (current and 3Y average)
- Net Debt / Market Cap
- Cash from Operations / Market Cap
- Capital Expenditure metrics
- P/B Ratio
- Share count changes
- Total returns
- Growth rates (CAGR for PP&E, Assets, CapEx)
- Cash and burn metrics

---

## Analysis Date & Versioning

Each output file includes:
- Timestamp in filename: `Junior_Miner_Analysis_V6_YYYYMMDD_HHMMSS.xlsx`
- Analysis_Date column in results
- Logged execution history in `analysis_log.txt`

This enables tracking changes over time and maintaining audit trails.

---

## Questions or Issues?

This framework is designed to be transparent and reproducible. All scoring logic is deterministic - running the same input data will always produce the same results.

For questions about specific company scores, refer to:
1. Individual factor scores to identify strengths/weaknesses
2. Raw KPI values to understand underlying metrics
3. Cluster assignment to see peer grouping
4. Profile analysis sheets for contextual percentile comparisons

**The goal**: Combine quantitative rigor with investment judgment to identify compelling opportunities in the junior mining space.
