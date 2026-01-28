# E-Waste Generation Modeling: Indonesian Data Center Sector

> Quantifying electronic waste from data centers in Indonesia using the Sales-Lifespan Distribution Model with Weibull probability distributions. This project segments modeling by operator tier (hyperscale vs. enterprise) to account for divergent refresh cycles driven by regulatory, economic, and energy cost factors.

## Project Overview

### Problem Statement
Indonesia's rapidly growing data center sector generates electronic waste with patterns distinctly different from global norms. Single-variable e-waste models fail to capture:
- **TKDN regulatory delays** extending equipment procurement timelines
- **Bifurcated energy tariffs** creating divergent refresh strategies
- **Asset sweating practices** in mid-market enterprises extending equipment life
- **Regulatory mandates** (OJK disaster recovery, ISO 14001) introducing acceleration factors

### Solution Approach
Implemented a tier-segmented **Sales-Lifespan Distribution Model** using Weibull probability distributions to project annual e-waste volumes with sector-specific parameter adjustments:
- Hyperscale operators: λ = 4.0 years (align with global standards)
- Enterprise/on-premises: λ = 5.5 years (reflect asset-sweating behavior)

## Key Findings

### Equipment Refresh Cycle Variance
| Equipment Type | Global Avg | Hyperscale (Indonesia) | Enterprise (Indonesia) |
|---|---|---|---|
| Servers (1U/2U) | 3–4 years | 3–4 years | 5–7 years |
| Storage Arrays | 4–5 years | 4–5 years | 6–8 years |
| Network Equipment | 5–7 years | 5–6 years | 7–10 years |
| Critical Power (UPS) | 10–15 years | 10–12 years | 12–15 years |


## Technical Implementation
- **Python** (pandas, numpy, scipy for Weibull distributions)
- **Jupyter Notebook** for exploratory analysis and visualization
- **Matplotlib/Seaborn** for lifecycle charts and projection graphs

## Methodology

### Sales-Lifespan Distribution Model
The fundamental equation:

$$E(t) = \sum_{n=1}^{N} P(t-n) \times L(n)$$

Where:
- **E(t)**: Total e-waste generated in year *t* (tonnes)
- **P(t−n)**: Quantity of equipment "Put On Market" *n* years ago (tonnes)
- **L(n)**: Lifespan probability function (Weibull CDF)
- **N**: Maximum observable lifespan (~15 years)

### Weibull Parameters (Indonesian Context)
- **Shape Parameter (k)**: 3.5 for all tiers (accelerating failure rate)
- **Scale Parameter (λ)**:
  - Hyperscale: 4.0 years
  - Enterprise: 5.5 years

### MW-to-Tonnes Conversion Sequence
1. Extract IT equipment power: `IT Power = Total Power / PUE` (PUE ~1.67 regional average)
2. Estimate rack count: `Racks = IT Power (MW) × 1,000 / 10 kW per rack`
3. Calculate equipment mass: `Mass = Racks × 1.13 tonnes per rack`

## Results Summary

### Key Outputs
- **Annual e-waste projections** (2020–2030) by operator tier and equipment category
- **Sector-level multiplier effects** (banking DR redundancy, manufacturing cycles)
- **Sensitivity analysis** on PLN tariff escalation and ISO 14001 adoption rates
- **Validation comparison** with licensed B3 waste operator collection records

## Key Insights for Sustainability

1. **Energy cost sensitivity matters**: Rp 996–1,114/kWh tariff differences create measurable economic incentives for refresh acceleration
2. **Regulatory paradox**: ISO 14001 certification paradoxically accelerates near-term e-waste (2025–2030) by 10–20% before reducing it long-term
3. **Sector-specific dynamics**: Banking sector generates 50–55% of e-waste vs. 35–40% of market revenue
4. **Data limitations**: B3 waste storage restrictions (90 days) create batch decommissioning patterns not captured by smooth Weibull curves

### Data Science & Analytics
- **Probability distributions** and statistical modeling (Weibull)
- **Time-series forecasting** with distributed lags
- **Sensitivity analysis** and parameter optimization
- **Data validation** against ground-truth records

### Domain Expertise
- **Sustainability sector knowledge** (e-waste, circular economy)
- **Energy systems understanding** (tariffs, efficiency, OpEx-CapEx tradeoffs)
- **Indonesia-specific regulatory context** (TKDN, OJK, B3 waste)
- **Data center operations** (lifecycle, refresh cycles, redundancy)

### Engineering & Communication
- **Research-grade documentation** with academic rigor
- **Reproducible notebooks** with clear methodology
- **Policy-relevant insights** for government and industry stakeholders
- **Complex technical concepts** explained accessibly
