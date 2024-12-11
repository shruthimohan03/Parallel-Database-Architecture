# Parallel Database Architecture

This project demonstrates the use of OpenMP to parallelize database operations, specifically querying and processing employee and performance metrics data.

## Parallelism Techniques

### Data Parallelism
* Achieved in the `processEmployeesAndMetricsByDepartment` function.
* Divides the task of querying and processing employees based on department among multiple threads using `#pragma omp section`.
* Each thread processes a portion of the data concurrently, improving performance.

### Task Parallelism/Query Parallelism
* Also implemented in `processEmployeesAndMetricsByDepartment`.
* Utilizes `#pragma omp parallel sections` to execute different code sections in parallel.
  * One section queries employees by department.
  * Another section processes the retrieved data.

### Architecture Parallelism
* OpenMP enables the code to execute concurrently on multiple processor cores.
* The `#pragma omp parallel sections` directive splits execution into threads, each utilizing a different core for concurrent processing.

## Code Breakdown

### Data Structures
* `Employee` and `PerformanceMetrics` structs define data structures for employee and performance data.

### Data Generation
* `generateEmployeesWithPerformance` function generates a dataset of employees and their performance metrics based on a specified number of employees.

### Parallel Processing Function
* `processEmployeesAndMetricsByDepartment` queries and processes data based on department.
  * Two sections are executed in parallel:
    * First section queries employees and populates `departmentData`.
    * Second section processes the data and prints details of each employee and their metrics.

### Main Function
* Generates a dataset and processes it using `processEmployeesAndMetricsByDepartment`.

## Performance Analysis
* Measures execution time for varying numbers of employees and processing elements (threads).
* Adjusts problem size (numEmployees) and processing elements (OMP_NUM_THREADS) to collect execution time data.
* Calculates speedup and parallel efficiency based on the data.

### Graphs
* **Graph 1:** Speedup vs. Processing Elements for different problem sizes (N).
![image](https://github.com/user-attachments/assets/b824a55f-7023-4f7c-bb6f-597ca6c6f91d)

* **Graph 2:** Speedup vs. Problem Size (N) for different processing elements.
![image](https://github.com/user-attachments/assets/9ed8a5db-6678-4c9f-95eb-054a43bdee30)

## Contributors
* [Shruthi Mohan](https://github.com/shruthimohan03)
* [Pravalika Arunkumar](https://github.com/pravalikaarunkumar)
