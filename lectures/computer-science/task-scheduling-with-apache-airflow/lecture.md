# Task Scheduling with Apache Airflow

Apache Airflow is a platform to programmatically author, schedule, and monitor workflows. Use it to author workflows as directed acyclic graphs (DAGs) of tasks. Here's how to define a simple DAG:

```python
from datetime import datetime
from airflow import DAG
from airflow.operators.dummy_operator import DummyOperator

dag = DAG('my_dag', start_date=datetime(2022, 1, 1))

start = DummyOperator(task_id='start', dag=dag)
end = DummyOperator(task_id='end', dag=dag)

start >> end
```
This DAG consists of two tasks (`start` and `end`). The `>>` operator signifies that `end` should run after `start`.

Airflow provides a rich set of built-in operators for many common tasks:

* `BashOperator` to execute bash commands
* `PythonOperator` to execute Python callables
* `EmailOperator` to send emails
* `SimpleHttpOperator` to send HTTP requests
* `MySqlOperator`, `SqliteOperator`, `PostgresOperator`, `MsSqlOperator`, `OracleOperator`, `JdbcOperator`, `RedshiftOperator` to execute SQL commands
* and many more

Here's a DAG that executes a Python function:

```python
from airflow.operators.python_operator import PythonOperator

def my_func():
    print("Hello, Airflow")

task = PythonOperator(task_id='my_task', python_callable=my_func, dag=dag)

start >> task >> end
```
The `PythonOperator` calls the `my_func` function when the task is run.

Tasks are instances of `BaseOperator`, and they're parameterized by a set of arguments and a collection of upstream and downstream tasks. You can use operators to express complex dependency structures between tasks, and Airflow will handle their scheduling and execution.

Airflow comes with a web-based user interface where you can monitor your workflows, retry failed tasks, and debug issues. You can also use it to trigger workflows manually or on a schedule.