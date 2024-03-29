Overview
========

Projeto de ETL/ELT
Extração de dados através de web scraping, Transformação de dados usando pandas e Load para banco de dados Postgres, Datalake e Data LakeHouse.

Tecnologias Utilizadas:
========

Astro-sdk Airflow
Minio
Postgres
Dremio

### Instalação e Configuração

1. Clone o repositório:

```bash
git clone https://github.com/claytoncampos/data-engineer-elt.git
cd data-engineer-elt
```

2. Configure a versão correta do Python com `pyenv`:

```bash
pyenv install 3.12
pyenv local 3.12

ou instale o poetry 
pip install poetry
```

3. Instale as dependências do projeto:

```bash
# Instale o Docker e docker-compose
# Intale o pyenv
pip install pyenv
# crie seu ambiente virtual
python -m venv .venv
# O padrao é utilizar .venv
source .venv/bin/activate
# Usuários Linux e mac
.venv\Scripts\Activate
# Usuários Windows
pip install -r requirements.txt 
# poetry
poetry install
 ```

Project Contents
================

Your Astro project contains the following files and folders:

- dags: This folder contains the Python files for your Airflow DAGs. By default, this directory includes two example DAGs:
    - `example_dag_basic`: This DAG shows a simple ETL data pipeline example with three TaskFlow API tasks that run daily.
    - `example_dag_advanced`: This advanced DAG showcases a variety of Airflow features like branching, Jinja templates, task groups and several Airflow operators.
- Dockerfile: This file contains a versioned Astro Runtime Docker image that provides a differentiated Airflow experience. If you want to execute other commands or overrides at runtime, specify them here.
- include: This folder contains any additional files that you want to include as part of your project. It is empty by default.
- packages.txt: Install OS-level packages needed for your project by adding them to this file. It is empty by default.
- requirements.txt: Install Python packages needed for your project by adding them to this file. It is empty by default.
- plugins: Add custom or community plugins for your project to this file. It is empty by default.
- airflow_settings.yaml: Use this local-only file to specify Airflow Connections, Variables, and Pools instead of entering them in the Airflow UI as you develop DAGs in this project.

Deploy Your Project Locally
===========================

1. Start Airflow on your local machine by running 'astro dev start'.

This command will spin up 4 Docker containers on your machine, each for a different Airflow component:

- Postgres: Airflow's Metadata Database
- Webserver: The Airflow component responsible for rendering the Airflow UI
- Scheduler: The Airflow component responsible for monitoring and triggering tasks
- Triggerer: The Airflow component responsible for triggering deferred tasks

2. Verify that all 4 Docker containers were created by running 'docker ps'.

Note: Running 'astro dev start' will start your project with the Airflow Webserver exposed at port 8080 and Postgres exposed at port 5432. If you already have either of those ports allocated, you can either [stop your existing Docker containers or change the port](https://docs.astronomer.io/astro/test-and-troubleshoot-locally#ports-are-not-available).

3. Access the Airflow UI for your local Airflow project. To do so, go to http://localhost:8080/ and log in with 'admin' for both your Username and Password.

You should also be able to access your Postgres Database at 'localhost:5432/postgres'.

4. Start Minio on your local machine by running 'docker-compose up minioserver -d'.

This command will spin up 1 Docker containers on your machine.

Acess the minio server, To do so, go to http://localhost:9000/ and log in with 'admin' for both your Username and Password.

5. Start Dremio on your local machine by running 'docker-compose up dremio -d'.

This command will spin up 1 Docker containers on your machine.

Acess the minio server, To do so, go to http://localhost:9047/ and log in with 'admin' for both your Username and Password.