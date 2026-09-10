# Seasonal-Agriculture-Performance-Analysis 

# Seasonal Agriculture Performance Analysis

Major project submitted for the VOIS AICTE program (Batch 2026-2027, Data Visualization track).

The idea behind this project is simple — agriculture in India runs on three seasons (Kharif, Rabi, Zaid), and each one comes with its own weather, its own crops and its own set of risks. This project looks at a dataset of 4,000 farm records and tries to figure out, with actual numbers instead of assumptions, how much of a difference the season really makes to yield, cost, profit and resource use.

## What's in this repo

| File | What it is |
|---|---|
| `Seasonal_Agriculture_Performance_Analysis.ipynb` | The main analysis — Jupyter notebook, Python |
| `seasonal_agriculture_performance_dataset.csv` | The raw dataset used for the analysis |
| `Major_Project_Seasonal_Agriculture_Performance_Analysis.pdf` | Original project brief given by VOIS/AICTE |
| `VOIS_Major_Project_PPT_Submission.pptx` | Slide deck summarizing the project for submission |

## Dataset

4,000 farm records across 8 states, 8 crops and 3 seasons. Each row has weather info (rainfall, temperature, humidity, sunlight), farming inputs (fertilizer, pesticide, seed quality, irrigation method), and outcomes (yield, production, cost, revenue, profit, disease/pest risk).

A small percentage of rows have missing values in Rainfall, Soil Moisture and Yield (roughly 1% each) — noted in the notebook rather than silently dropped.

## Approach

Nothing fancy — mostly Pandas for grouping/aggregating by season, and Matplotlib/Seaborn for the charts. The notebook goes through:

- Basic exploration (shape, types, missing values, duplicates)
- Season-wise comparison of weather conditions
- Yield and production by season
- Cost, revenue, profit and how many farms are actually running at a loss
- Water/fertilizer/pesticide usage and irrigation method preference by season
- A correlation check between environmental/input variables and yield/profit
- Crop-wise and state-wise breakdown (season averages can hide a lot, so this digs a level deeper)
- Disease/pest risk by season

## A few things that came out of the analysis

- **Kharif has the highest average yield (5.64 t/ha), Zaid the lowest (4.67 t/ha).** The gap isn't huge, but it's consistent.
- **Profitability is where the seasons really diverge.** Kharif farms average a profit of ~₹1.79L, Rabi ~₹0.88L, and Zaid actually comes out *negative* on average (~-₹25K). More than 64% of Zaid farms are running at a loss, vs 42% in Kharif.
- **Yield correlates decently with profit (0.49) and water use (0.39)**, but barely with anything else — fertilizer, rainfall, soil pH etc. all show weak correlations. So there isn't one obvious lever that explains performance; it's a mix of a lot of small things.
- **Irrigation method mix doesn't shift much by season** — Flood stays the most common (~32-33%) across all three, which was a bit surprising going in.
- **Disease/pest risk is clearly highest in Kharif (54.5%)** compared to Rabi (40.5%) and Zaid (38.2%) — makes sense given the humidity that comes with the monsoon.
- Crop-wise, the Kharif > Rabi > Zaid yield pattern holds for basically every crop in the dataset, but profit by state is a lot less consistent — some states (Punjab, Karnataka) stay profitable in Zaid while others (Gujarat, Andhra Pradesh) go well into the red.

Correlation is used here only as a first screening step — it shows association, not causation, so none of the above should be read as "X causes Y."

## Running it yourself

```bash
git clone https://github.com/chitranjan-7-8-6/Seasonal-Agriculture-Performance-Analysis.git
cd Seasonal-Agriculture-Performance-Analysis
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter notebook Seasonal_Agriculture_Performance_Analysis.ipynb
```

Just make sure the CSV is in the same folder as the notebook before running it top to bottom.

## Tools used

Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy — all inside a Jupyter Notebook.

## Where this could go next

- A proper ML model to predict yield/profit instead of just describing patterns
- Pulling in live weather data instead of a static snapshot
- Going down to district/village level instead of state level — state averages hide a lot
- Digging into *why* so many farms are unprofitable, since that shows up in every season, not just Zaid

## Author

Chitranjan Vishwakarma — BCA student, Sri Ram Kishun P.G. College (Gokul, Karsada, Varanasi)

Submitted as part of the VOIS AICTE Data Visualization major project.
