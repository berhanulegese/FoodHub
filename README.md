# FoodHub EDA

Exploratory data analysis (EDA) to help a food aggregator understand demand patterns across restaurants and cuisines, and identify levers to improve customer experience and business performance. The analysis investigates what customers order, when they order, how much they spend, and how operational timings (prep and delivery) relate to satisfaction (ratings).

## What This Project Does

- Quantifies demand by cuisine and restaurant (orders, share, spend proxy).
- Analyzes ordering patterns across weekdays vs weekends.
- Profiles spend behavior (average order value, distribution, outliers).
- Studies operational timings: preparation vs delivery time, and their correlation.
- Examines ratings (including missing “Not given”) and relationships to timings and cost.
- Surfaces high- and low-performing cuisines/restaurants for targeted actions.

## Dataset

Source: `foodhub_order.csv` (included). Columns:

- `order_id`: Unique order identifier.
- `customer_id`: Customer identifier (enables basic customer-level aggregation).
- `restaurant_name`: Restaurant fulfilling the order.
- `cuisine_type`: Cuisine for the restaurant/order.
- `cost_of_the_order`: Basket value for the order.
- `day_of_the_week`: `Weekday` or `Weekend` (ordering context).
- `rating`: Customer rating or `Not given` when missing.
- `food_preparation_time`: Minutes spent preparing the order.
- `delivery_time`: Minutes spent delivering the order.

Notes and assumptions:

- Ratings contain a `Not given` category, treated as missing and profiled separately.
- Monetary values are used comparatively (e.g., average order value) rather than as audited revenue.
- No geolocation or exact timestamps are present; time-of-day and distance effects are not modeled.

## Business Questions Addressed

- Which cuisines and restaurants drive the most orders and spend?
- How do weekday and weekend demand patterns differ?
- What is the typical order value and its variance across cuisines/restaurants?
- How do preparation and delivery times interact, and where are the bottlenecks?
- Do longer prep/delivery times correlate with lower ratings?
- Which areas present opportunities (e.g., slow but popular, fast but low-rated)?

## Analysis Outline (in the Notebook)

1. Load and inspect data; handle missing values (ratings).
2. Sanity checks and type conversions where needed.
3. Univariate profiles: cuisines, restaurants, spend, timings, ratings.
4. Bivariate analysis: timings vs ratings; cost vs cuisine/restaurant; weekday vs weekend.
5. Ranking/segmentation: top cuisines/restaurants by orders and average order value.
6. Operational insights: identifying slow prep or delivery clusters for improvement.
7. Recommendations: data-backed actions for menus, promotions, and operations.

## Outputs

- Interactive notebook: `Food Hub Full Code.ipynb` (main analysis).
- HTML export: `Full-Code-version.html` (viewable without running code).
- Visuals: charts rendered in the notebook (optionally exportable to a `reports/` folder).

## Repository Contents

- `Food Hub Full Code.ipynb` — main analysis notebook (originally authored in Google Colab).
- `Full-Code-version.html` — static HTML export of the notebook (viewable in any browser).
- `foodhub_order.csv` — dataset used by the analysis.

## Requirements

- Python 3.8+ (3.10 recommended)
- Packages: `numpy`, `pandas`, `matplotlib`, `seaborn` (and optionally `jupyter` for running notebooks)

Install packages with:

```
pip install --upgrade pip
pip install numpy pandas matplotlib seaborn jupyter
```

Optional (recommended) virtual environment:

```
# create and activate a venv
python -m venv .venv
# Windows PowerShell
.\.venv\Scripts\Activate
# macOS/Linux
source .venv/bin/activate
```

## Running the Analysis Locally

1) Open the notebook:

```
jupyter notebook
# or
jupyter lab
```

2) In `Food Hub Full Code.ipynb`, use the local CSV path. Replace any Colab Drive path with the file that ships in this repo:

```python
import pandas as pd

# Preferred (local) path
df = pd.read_csv('foodhub_order.csv')

# If you still want a Colab fallback, you can use:
# import os
# local = 'foodhub_order.csv'
# if os.path.exists(local):
#     df = pd.read_csv(local)
# else:
#     df = pd.read_csv('/content/drive/My Drive/Python Course/foodhub_order.csv')
```

3) Run cells top-to-bottom to reproduce the EDA and figures.

## Viewing Without Running Code

Open `Full-Code-version.html` directly in your browser to read the analysis and see outputs without executing the notebook.

## Common Issues

- File not found: Ensure you point to `foodhub_order.csv` in the project root when running locally. If using Colab, either upload the CSV to the session or mount Drive and update the path accordingly.
- Package errors: Verify packages are installed in the same environment/kernel used by Jupyter.

## Next Steps (Optional)

- Convert the notebook to a Python script for headless runs:

```
jupyter nbconvert --to script "Food Hub Full Code.ipynb"
```

- Organize outputs (figures/tables) into a `reports/` folder if you plan to export plots.

---

Questions or contributions are welcome.
