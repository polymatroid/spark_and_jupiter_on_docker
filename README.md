# Spark and Jupyter on Docker

This repository is intended for testing and learning Spark locally on your PC through Docker containers.

Currently spark running based on master container and one worker container , additional worker could be added in docker-compose.yaml file.

## Getting Started

Follow these steps to get up and running:

### 1. Build Docker Images

Run the following command to build the Docker images:

```bash
docker-compose build
```

### 2. Start the Containers

Use the command below to start the Docker containers:

```bash
docker-compose up
```

### 3. Access Spark Web UI

Navigate to [http://localhost:9090/](http://localhost:9090/) to access the Spark web UI.

### 4. Access JupyterLab

Visit [http://localhost:8888](http://localhost:8888) to access JupyterLab. On your first visit, you’ll need to use a token:

- **Find the Token:** Check the Docker logs for a URL with the token, which will look like:
  ```
  http://127.0.0.1:8888/?token=c158e5352ec05fe944e47a903016da0a536e412cd6e1f6d7
  ```

- **Alternatively:** Enter the Docker container and run:
  ```bash
  jupyter server list
  ```
  Copy the token and use it to log in at [http://localhost:8888](http://localhost:8888).

## Running PySpark Code

### From Your PC

To execute a Python script directly from your PC, use:

```bash
docker-compose exec spark-master spark-submit --master spark://spark-master:7077 scripts/your_script.py
```

Replace `your_script.py` with the name of your script.

File scripts consists example of pyspark code.

### From Jupyter Notebook

To run PySpark code in a Jupyter notebook, use:

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("JupyterLab-Spark") \
    .master("spark://spark-master:7077") \
    .getOrCreate()
```
Jupyter notebooks mounted to directory data in this repo.