# Cleanstream: A Lightweight Python ETL Pipeline in Docker

Cleanstream is a minimal, containerized Python ETL pipeline that demonstrates how to extract, transform and load (ETL) data using Pandas. It is ideal for learning or bootstrapping custom data pipelines in a reproducible environment. This was built as a basic project by me to understand how data pipelines work. 

## Features

- Dockerized ETL workflow
- CSV-based data ingestion and transformation
- Simple and extensible project structure
- Easy customization for different datasets

## Prerequisites

- Docker installed and running
- Git (optional, for cloning the repository)

## Getting Started

1. Clone the repository:

   ```
   git clone https://github.com/geheimerr/CleanStream.git
   cd CleanStream
   ```
3. Build and run the container:

   ```
   docker-compose up --build
   ```

   This will:
   - Build the Docker image
   - Install required packages from requirements.txt
   - Execute the pipeline.py script inside the container

## Customizing for Your Dataset

To run the pipeline on your own data:

1. Copy your dataset (CSV format) into the `app/` directory:

   ``` cp /path/to/your_dataset.csv app/ ```

2. Edit `pipeline.py` to use your dataset:

   Replace:
      ``` df = pd.read_csv("medicaldataset.csv") ```
   With:
    ```   df = pd.read_csv("your_dataset.csv") ```

3. Add your own transformation logic in the same script.

4. Rebuild and rerun the container:

   ``` docker-compose up --build ```

## Example: Basic Transformation

A sample transformation in `pipeline.py` might look like this:

   ```
   import pandas as pd

   df = pd.read_csv("your_dataset.csv")
   df.dropna(inplace=True)
   df["BMI"] = df["Weight"] / ((df["Height"] / 100) ** 2)
   df.to_csv("output.csv", index=False)
```

## Notes

- Do not commit large or sensitive datasets to the repository.
- You can extend the pipeline to support other data formats, load targets (e.g. databases), or schedule it using cron or Airflow.

## License

This project is licensed under the MIT License.

