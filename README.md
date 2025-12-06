# FoodHub EDA

Exploratory data analysis (EDA) for a food aggregator to understand demand across restaurants and cuisines, with the goal of improving customer experience and business performance.

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
