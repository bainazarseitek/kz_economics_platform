# Kazakhstan Economics Platform

An interactive analytics platform for exploring Kazakhstan’s regional economy, infrastructure investment, sector importance, and experimental geospatial indicators.

## 1st Place — 2024 Data Challenge

Our team placed **1st out of 144 teams** in the 2024 Data Challenge organized by [DataSci](https://www.linkedin.com/company/datasci-kz/) and the [Development Bank of Kazakhstan](https://www.linkedin.com/company/dbkkz/). Over one week, we built an AI-powered platform to support decisions about Kazakhstan's economic growth and infrastructure investment.

This repository is a public portfolio snapshot of that collaborative work. It preserves the application, analysis, and reproducible experiment results while omitting team member names and personal details.

## What it does

- Displays Kazakhstan’s regions on an interactive map.
- Explores historical infrastructure investment by region and economic sector.
- Produces five-year exploratory forecasts from historical series.
- Ranks sector importance using statistical and machine-learning models.
- Supports automatic and manual investment-impact simulations.
- Visualizes regional and national economic indicators.
- Experiments with YOLO-based satellite-image segmentation for roads, damage, water, methane, agriculture, and other infrastructure features.

## Architecture

```text
Next.js + React dashboard
          |
          v
FastAPI analytics API
          |
          +-- pandas / statsmodels forecasting
          +-- scikit-learn ranking and simulation
          +-- processed regional workbooks

Separate research notebooks
          +-- economic analysis
          +-- YOLO geospatial segmentation
```

## Run the dashboard

### Backend

Use Python 3.10 or 3.11 for compatibility with the original pinned analytics stack.

```bash
cd dashboard_platform/server
python3.11 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn server:app --port 8080 --reload
```

The API will be available at <http://127.0.0.1:8080>; interactive API documentation is at <http://127.0.0.1:8080/docs>.

### Frontend

In a second terminal:

```bash
cd dashboard_platform/client
npm ci
npm run dev
```

Open <http://127.0.0.1:3000>.

## Repository guide

| Path | Purpose |
|---|---|
| `dashboard_platform/client/` | Next.js, React, Mantine, Chart.js, and map interface |
| `dashboard_platform/server/` | FastAPI endpoints, forecasting, rankings, simulations, and processed runtime data |
| `analysis/` | Economic-analysis notebooks and statistical scripts |
| `ml/GeospatialAI/` | Satellite-segmentation notebook and recorded training metrics |

## Geospatial experiment

The recorded segmentation experiment used YOLO11 on a small annotated satellite-image dataset. Its original notebook reports **23.85% mAP@0.5** on the validation split. This is an early prototype result, not evidence of production-level generalization.

Raw satellite imagery and trained weights are not distributed in this portfolio repository. The dataset was prepared through [Roboflow Universe](https://universe.roboflow.com/teamx/geospatial-ai/dataset/1) and marked CC BY 4.0 by its publisher. Obtain authorized data and model weights separately before reproducing the experiment.

## Data and limitations

Processed workbooks required by the dashboard are included. Raw source archives, generated training samples, notebook outputs, and large model checkpoints are excluded from the public snapshot.

This is a Data Challenge prototype. Forecasts and simulated economic effects are exploratory, depend on limited historical data, and should not be treated as official statistics or policy recommendations. Production use would require source-level data validation, broader model evaluation, security review, and monitoring.

## Licensing

No project-wide license is granted. Unless a file contains its own license notice, the material in this repository may be viewed but not copied, modified, or redistributed without permission from the project contributors. Third-party datasets, libraries, and model weights remain subject to their respective licenses.
