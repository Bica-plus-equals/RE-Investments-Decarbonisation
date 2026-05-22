# Overview
The core of this work involves modeling various renewable energy technologies. It uses financial data such as Capital Expenditure (CAPEX), Operational Expenditure (OPEX), project lifetime, and estimated discount rates to predict the profitability of different technologies. Additionally, it includes a sustainability assessment that considers future decarbonization pathways and policy impacts.

**Note:** this model is currently undergoing updating to replace the data and improve accuracy. Part I of the model is the updated one. Part II is based on simulated data, and may not be representative of real behaviour. 

## Dataset
The analysis uses IEA data on the costs of generating electricity from 2020. The dataset contains techno-economic data on different energy generation technologies. This analysis processes the excel-style formatting to extract necessary data for a simple financial analysis on broad horizons. 
The dataset mainly contains Capacity and CAPEX data. A few modelling assumptions are made to forecasting revenue from energy generation. 

## Modelling Assumptions
Some parameter approximations are made using generative AI to estimate OPEX percentages, capacity factors (which after cross-checking with IEA seem reasonable with a 0-0.5% error margin). Electricity price is simplified to the average annual price over Europe , which by Eurostat is ~ €0.2896/kWh =  0.31/kWh= 310/MWh (Ref: [Eurostat](https://www.google.com/url?q=https%3A%2F%2Fec.europa.eu%2Feurostat%2Fstatistics-explained%2Findex.php%3Ftitle%3DElectricity_price_statistics))

## Model and Methods
### ROI forecasting
A DCF (discounted cash flow) model is used to generate a Return of Investment timeline by technology. 
![My diagram](ROI Plot1.png)

### Marginal Abatement Cost Curve (Old version)
The project utilizes Marginal Abatement Cost Curves (MACC) to identify the most cost-effective ways to reduce CO2 emissions. Key elements of this analysis include:

- Technology: A range of renewable technologies like Solar PV, Onshore Wind, Biomass, Nuclear, and Carbon Capture Usage and Storage (CCUS).
Segment Type: Technologies are divided into different segments based on their cost and technological maturity.
- Segment Potential: The potential CO2 abatement for each segment.
- Marginal Cost: The cost associated with abating an additional unit of CO2.
- Cumulative Potential: The total emissions abated by combining various technology segments.
The MACC curve visually represents the cost of abating CO2 against the cumulative abatement potential, helping to prioritize investments.

### Market Influences
The project considers dynamic market conditions that can influence ROI, such as:

Carbon Price Increases: Simulating scenarios where carbon prices escalate over time.
Dynamic CAPEX: Accounting for technology learning rates, where CAPEX decreases over time (e.g., as seen in solar PV).
Policy Incentives: Evaluating the impact of subsidies on effective CAPEX.
### Monte Carlo Sensitivity Analysis
A crucial part of the project is the Monte Carlo simulation, which assesses the sensitivity of profitability to uncertainties in key variables. It involves:

1. Sampling Variables: Randomly sampling CAPEX factors, carbon prices, and discount rates within defined distributions.
2. Vectorized Calculations: Performing LCOA and revenue calculations for thousands of iterations.
3. Distribution Analysis: Examining the distribution of LCOA and revenue for each technology segment.
4. Profitability Probability: Calculating the probability of a technology being profitable (LCOA < 0) and how this probability changes under different carbon price scenarios (low, medium, high).


## Results (so far)
At the moment the model does not include carbon taxes, hence fossil-based resources have an overestimated ROI. 
