# Intelligent Cloud Resource Orchestrator using AI (ICRO-AI)

This project predicts cloud-like workload metrics (simulated) using a Machine Learning model
and generates auto-scaling decisions (scale up / scale down / keep) based on predicted load.
It also provides a Streamlit dashboard to visualize metrics, predictions, and scaling actions.

> NOTE: By default, this project **simulates** cloud behaviour. The `cloud_api.py` file contains
> placeholder functions where you can later integrate real AWS / Azure / GCP SDK calls if desired.

## Features

- Synthetic workload metrics generator (CPU utilization)
- ML-based workload forecasting using a regression model
- Simple rule-based auto-scaling policy driven by predictions
- Streamlit dashboard for visualization and manual experimentation
- Dockerfile for containerized deployment

## Project Structure

```text
ICRO-AI/
  README.md
  requirements.txt
  dockerfile
  dataset/
    sample_metrics.csv
  models/
    (model files will be saved here after training)
  src/
    simulate_metrics.py
    data_preprocessing.py
    train_model.py
    predict_load.py
    autoscaler.py
    cloud_api.py
    config.py
  dashboard/
    app.py
```

## Quick Start (Without Docker)

1. Create and activate a virtual environment (optional but recommended):

```bash
cd ICRO-AI
python -m venv venv
# Windows: venv\Scripts\activate
# Linux/Mac: source venv/bin/activate
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. (Optional) Regenerate synthetic dataset:

```bash
python src/simulate_metrics.py
```

4. Train the model:

```bash
python src/train_model.py
```

5. Run the dashboard:

```bash
streamlit run dashboard/app.py
```

Then open the URL shown in the terminal (usually http://localhost:8501).

## Run with Docker

```bash
docker build -t icro-ai .
docker run -p 8501:8501 icro-ai
```

Then open http://localhost:8501 in your browser.

## Disclaimer

This project is educational and research-oriented, not production-ready.
Real cloud integrations must be done carefully with proper authentication,
security and cost controls.
