# Airflow DAG Factory Castor

This project is a test of the [airflow-castor](https://github.com/castor-team/airflow-castor) project that creates DAGs dynamically using YAML files.

## Pre requisites
* Install [Docker Community Edition (CE)](https://docs.docker.com/engine/install/) on your workstation. Depending on the OS, you may need to configure your Docker instance to use 4.00 GB of memory for all containers to run properly. Please refer to the Resources section if using [Docker for Windows](https://docs.docker.com/docker-for-windows/#resources) or [Docker for Mac](https://docs.docker.com/docker-for-mac/#resources) for more information.
* Install [Docker Compose](https://docs.docker.com/compose/install/) v1.27.0 and newer on your workstation.

## Docker set up
For the first run, you need to run the command below to run the database setup and first user creation.
```
$ cd airflow-dag-factory/docker
airflow-dag-factory/docker$ docker-compose up airflow-init
```
After this command runs, you should see a message like below.
```
airflow-init_1       | Upgrades done
airflow-init_1       | Admin user airflow created
airflow-init_1       | 2.1.1
start_airflow-init_1 exited with code 0
```

To start the services you need to run the command below.
```
airflow-dag-factory/docker$ docker-compose up -d
```

To stop the services:
```
airflow-dag-factory/docker$ docker-compose down
```

### Services within docker-compose
* airflow-scheduler - The scheduler monitors all tasks and DAGs, then triggers the task instances once their dependencies are complete.
* airflow-webserver - The webserver available at http://localhost:8080.
* airflow-worker - The worker that executes the tasks given by the scheduler.
* airflow-init - The initialization service.
* flower - The flower app for monitoring the environment. It is available at http://localhost:5555.
* postgres - The database.
* redis - The redis - broker that forwards messages from scheduler to worker.

You can find more information about the services on this page: https://airflow.apache.org/docs/apache-airflow/2.1.1/start/docker.html#initializing-environment

## Access Airflow UI
Access the link http://localhost:8080 and insert the credentials below:
* User: airflow
* Password: airflow

