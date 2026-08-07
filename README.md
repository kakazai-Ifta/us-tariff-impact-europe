# The Impact of U.S. Tariff Changes on the German Economy

A data analysis project examining how the 2025 U.S. tariff measures affected trade flows, sectoral exposure, and macroeconomic conditions in Germany — the European Union's largest exporter to the U.S. market.

**Authors:** Ifta Kakazai, Hamza Boukhatem, Mame Ndiaye
**Department of Economics, Ca' Foscari University of Venice**

---

## Overview

In 2025, the United States implemented a series of tariff increases affecting most of its major trading partners, including the European Union. This project moves beyond the political narrative around those tariffs and quantifies their actual footprint using trade, tariff, and macroeconomic data covering 2020–2026.

Germany was chosen as the case study because it is consistently the EU's largest single exporter to the U.S., making it the most informative country for assessing the real economic impact of the tariff changes.

The analysis addresses five questions:

1. How large was the effective tariff burden across the U.S.'s top trading partners?
2. Which German export sectors are most exposed to U.S. tariff policy?
3. How did German exports to the U.S. behave month-by-month once tariffs took effect?
4. Did the tariffs cause Germany's trade to reallocate toward other partners (e.g., China)?
5. What was the broader macroeconomic impact — on policy uncertainty, GDP growth, and employment?

## Key Findings

- **Tariff burden:** U.S. imports across the analyzed products rose from ~$308B (2020) to ~$511B (2024); implied tariff revenue grew ~36% over the same period. Despite smaller import volumes, the EU (3.10%) and Brazil (3.40%) faced markedly higher effective tariff rates than Canada (1.40%) and Mexico (2.66%).
- **Sectoral exposure:** Motor vehicles and motor vehicle parts are Germany's largest export category to the U.S., meaning Germany's overall tariff exposure is closely tied to its automotive sector.
- **Monthly trade impact:** German exports to the U.S. fell as much as −21.2% year-on-year (July 2025) after tariffs took effect, before partially stabilizing once a negotiated ~15% baseline tariff was reached.
- **Trade reallocation:** China overtook the United States as Germany's largest trading partner by turnover in 2025.
- **Macroeconomic effects:** U.S. Economic Policy Uncertainty nearly tripled (mean of 133 in 2020–2024 to 383 in 2025–2026); German GDP growth slowed and employment growth flattened, particularly in manufacturing.

The full write-up, methodology, and figures are in [`Tariff_Impact_Report.pdf`](./Tariff_Impact_Report.pdf).

## Repository Structure

```
.
├── Project_CS2026.ipynb / .py     # Full analysis notebook (data cleaning, merging, and visualization)
├── Tariff_Impact_Report.pdf       # Final written report (LinkedIn/academic-style, 3 pages)
├── README.md                      # This file
└── data/                          # Raw input datasets (not included — see Data Sources below)
```

> Note: the notebook was developed in Google Colab and reads inputs from a mounted Google Drive path (`/content/drive/MyDrive/...`). To run it locally, download the datasets listed below and update the file paths, or place them in a local `data/` folder and adjust the `read_csv`/`read_excel` calls accordingly.

## Data Sources

| Dataset | Description | Format |
|---|---|---|
| ADB Imports | Bilateral U.S. import values by product/partner | CSV |
| ADB Exports | Bilateral U.S. export values by product/partner | CSV |
| ADB MFN Applied Duty | Most Favored Nation tariff schedules | CSV |
| Agricultural/Non-agricultural import indicators | Sector-level import breakdowns | CSV |
| Sector-Wise Export (2024/2025) | Germany's export values by sector | Excel |
| Country-Wise Export/Import (2024/2025) | Germany's bilateral trade by country | Excel |
| DEEPUINDXM | Germany Economic Policy Uncertainty Index (FRED) | CSV |
| USEPUINDXD | U.S. Economic Policy Uncertainty Index (FRED) | CSV |
| CLVMNACSCAB1GQDE | Germany quarterly real GDP (FRED) | CSV |
| Employment growth by industry | Germany, by sector and quarter | CSV |
| Employment in persons | Germany, aggregate employment | CSV |

Sources: WTO/ADB Trade and Tariff Indicators Database, Federal Reserve Economic Data (FRED), and the Federal Statistical Office of Germany (Destatis). See the report's References section for full citations.

## Methodology

1. **Load & clean** — import, export, and tariff datasets are loaded, renamed, and filtered (e.g., excluding "World" as a partner).
2. **Merge** — import, export, and tariff data are merged on `year` and `product_code`.
3. **Derive metrics** — an implied `tariff_value` (import value × tariff rate) and effective tariff rate are computed per partner; trade series are split into a pre-tariff period (2020–2024) and post-tariff period (2025–2026) for comparison.
4. **Visualize** — trade, tariff, sectoral, trade-turnover, EPU, GDP, and employment trends are charted using Matplotlib/Seaborn.
5. **Interpret** — each set of charts is discussed in the accompanying report, tying the data back to the tariff-policy questions above.

## Requirements

```
python >= 3.9
numpy
pandas
matplotlib
seaborn
openpyxl        # required for pd.read_excel on .xlsx files
```

Install with:

```bash
pip install numpy pandas matplotlib seaborn openpyxl
```

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/kakazai-Ifta/us-tariff-impact-europe.git
   cd us-tariff-impact-europe
   ```
2. Place the required datasets (see [Data Sources](#data-sources)) in a local folder and update the file paths at the top of each section of `project_cs2026.py` (originally set to a Google Drive path).
3. Run the script or open it as a notebook:
   ```bash
   python project_cs2026.py
   ```
   or convert it back to a notebook with `jupytext`/Colab and run cell by cell.
4. Generated charts correspond to the figures referenced in `Tariff_Impact_Report.pdf`.

## Report

The full report — abstract, methodology, findings, and references — is available in [`Tariff_Impact_Report.pdf`](./Tariff_Impact_Report.pdf).

## License

Add a license of your choice (e.g., MIT) if you intend for others to reuse this code.

## Authors

- Ifta Kakazai
- Hamza Boukhatem
- Mame Ndiaye

Department of Economics, Ca' Foscari University of Venice — Data Analysis Project (Computer Programming and Data Management course).
