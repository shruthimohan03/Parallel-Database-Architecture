# Parallel-Database-Architecture

1. Data Parallelism:
- Data parallelism is achieved in the processEmployeesAndMetricsByDepartment function, where the task of querying and processing employees based on department is divided among multiple threads.
- In the initial section, the employees are queried based on department in parallel using the #pragma omp section directive.
- Each thread operates on a different portion of the data, allowing multiple employees to be processed simultaneously.

2. Task Parallelism:
- Task parallelism is also utilized in the processEmployeesAndMetricsByDepartment function, where different sections of code are executed in parallel.
- Two sections are defined using #pragma omp parallel sections.
  - In the first section, employees are queried based on department.
  - In the second section, the queried data is processed.

3. Architecture Parallelism:
- OpenMP enables architecture parallelism by allowing the code to execute concurrently on multiple cores of the underlying processor architecture.
- The #pragma omp parallel sections directive in the code splits the execution of different sections of code into multiple threads, which can execute concurrently on different processor cores.
- Each thread executes a different section of code, harnessing the processing power of multiple cores simultaneously.

4. Code Description:
- The Employee and PerformanceMetrics structs represent the data structure for employees and their performance metrics.
- The generateEmployeesWithPerformance function generates a dataset of employees and their performance metrics based on the specified number of employees.
- The processEmployeesAndMetricsByDepartment function queries and processes employees and their performance metrics based on a specified department.
- Within this function, two sections are executed in parallel:
  - The first section queries employees based on department and populates the departmentData vector.
  - The second section processes the queried data and prints the details of each employee and their performance metrics.
- In the main function, a dataset is generated and then processed using the processEmployeesAndMetricsByDepartment function.
  
5. Performance Metrics:
To analyze the performance of this code, you can measure the execution time for different problem sizes (number of employees) and different numbers of processing elements (threads).
By varying the problem size (numEmployees) and the number of processing elements (through environment variables like OMP_NUM_THREADS), you can collect data on execution time.
Using this data, you can calculate speedup and parallel efficiency for different problem sizes and numbers of processing elements.
Graphs:

Graph 1: Plot speedup with respect to the number of processing elements for different problem sizes (N).
Graph 2: Plot speedup with respect to N for different numbers of processing elements.
Overall, this code demonstrates the use of OpenMP to achieve data and task parallelism, allowing for efficient processing of large datasets.
