# cuDF vs Pandas: Performance Comparison on Flight Data

This repository contains a performance comparison between **cuDF** and **Pandas** for analyzing flight data, specifically comparing execution times for various flight-related queries. The comparison demonstrates the scalability and efficiency of cuDF in processing large datasets, despite the additional setup challenges.

## Requirements

- **Python 3.x**
- **cuDF**: GPU-accelerated DataFrame library by RAPIDS
- **Pandas**: Python DataFrame library
- **Dask**: Parallel computing framework
- **Dask-CUDA**: Dask extension for GPU clusters
- **NVIDIA GPU** (for cuDF and Dask-CUDA)

To install the necessary dependencies, use the following:

```bash
# Install cuDF and Dask-CUDA
conda install -c rapidsai -c nvidia -c conda-forge \
    cudf=21.06 dask-cuda=21.06 dask-cudf=21.06 \
    dask distributed pandas
```
## Setup
This project uses Dask-CUDA for running cuDF operations on multiple GPU workers.

Ensure you have access to a CUDA-enabled GPU.
Initialize the Dask cluster using LocalCUDACluster.
Load the flight data (CSV format) with cuDF and Dask.
Dataset
flights_file: CSV file containing flight data.
carriers_file: CSV file containing information about flight carriers.
Benchmark Functions
Several benchmark functions are defined to measure execution times for operations such as:

Max arrival delay by carrier
Day with the most flights
Most cancellations by carrier
Most miles flown
Best recovery from delays
Growth in the number of flights per year
Cancellations by month
Cancellation percentage per month
Both cuDF and Pandas implementations of these functions are provided to compare performance.

## Notes
cuDF demonstrated significant speed improvements for most tasks, especially in large datasets.
Pandas had slightly better performance for tasks involving cancellations per flight, but cuDF outperformed Pandas in most of the other tasks, especially with large data volumes.
Setting up cuDF with Dask-CUDA presented challenges, including version incompatibilities and initial configuration difficulties.
