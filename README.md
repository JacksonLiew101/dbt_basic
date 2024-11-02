**dbt basic 1 **
====================

This repository emulates an “open-source” project, though exclusively shared within the dataexpert community. Members can access the repository for independent use or contribute enhancements to the project's design and functionality. This serves as an opportunity to practice contributing to publicly shared open-source repositories.

**Table of Contents**


- [🚀 Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Local Development](#local-development)
  - [dbt Project Setup](#dbt-project-setup)
- [📚 Other Helpful Resources for Learning!](#-other-helpful-resources-for-learning)
- [📂 Navigating the Repository](#-navigating-the-repository)


# **🚀 Getting Started**

## **Prerequisites**

1. **Python >= 3.9**

## **Local Development**

1. **Clone the Repository**: Open a terminal, navigate to your desired directory, and clone the repository using:
    ```bash
    git clone git@github.com:DataExpert-io/dbt-basics.git # clone the repo
    cd dbt-basics # navigate into the new folder
    ```

    1. If you don’t have SSH configured with the GitHub CLI, please follow the instructions for [generating a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?tool=cli) in the GitHub docs.



## dbt Project Setup

-  **Create a Branch:**
    - Navigate to the **`dbt-basics`** repo on your local machine.
    - Use the **`git checkout -b`** command to create a new branch where you can commit and push your changes. Prefix your branch name with your Git username to avoid conflicts.
          For example:

        ```bash
        git checkout -b student/my-git-username
        ```

- Create a venv to isolate required packages
  ```bash
  python3 -m venv venv # MacOS/Linux
  # or
  python -m venv venv # Windows/PC
  ```
- Source the virtual environment
  ```bash
  source venv/bin/activate # MacOS/Linux
  # or
  venv/Scripts/activate # Windows/PC
  ```
- Install the required packages
  ```bash
  pip3 install -r dbt-requirements.txt # MacOS/Linux
  # or
  pip install -r dbt-requirements.txt # Windows/PC
  ```
- Update `DBT_SCHEMA` environment variable
  - MacOS/Linux:
    - Open the `dbt.env` file, change the `DBT_SCHEMA` to your schema from Weeks 1 and 2, and source the environment variables to your local (terminal) environment
      ```bash
      export DBT_SCHEMA='your_schema' # EDIT THIS FIELD
      ```
    - then run
      ```bash
      source dbt.env
      ```
  - Windows/PC:
    - Instead of overwriting the DBT_SCHEMA in the file you can run:
      - CMD:
      ```bash
      set DBT_SCHEMA=your_schema

      # For example
      set DBT_SCHEMA=john #(without quotes)
      ```
      - PowerShell:
      ```bash
      $env:DBT_SCHEMA = "your_schema"

      # For example
      $env:DBT_SCHEMA = "john"
      ```


- Run `dbt debug` to check your connection. You should see a message like this:
    ```
    13:43:43  Running with dbt=1.9.0-b3
    13:43:43  dbt version: 1.9.0-b3
    13:43:43  python version: 3.9.6
    13:43:43  python path: .../dbt-basics/venv/bin/python3
    13:43:43  os info: macOS-15.1-arm64-arm-64bit
    13:43:44  Using profiles dir at .
    13:43:44  Using profiles.yml file at ./profiles.yml
    13:43:44  Using dbt_project.yml file at ./dbt_project.yml
    13:43:44  adapter type: snowflake
    13:43:44  adapter version: 1.8.4
    13:43:44  Configuration:
    13:43:44    profiles.yml file [OK found and valid]
    13:43:44    dbt_project.yml file [OK found and valid]
    13:43:44  Required dependencies:
    13:43:44   - git [OK found]

    13:43:44  Connection:
    13:43:44    account: aab46027.us-west-2
    13:43:44    user: dataexpert_student
    13:43:44    database: DATAEXPERT_STUDENT
    13:43:44    warehouse: COMPUTE_WH
    13:43:44    role: ALL_USERS_ROLE
    13:43:44    schema: john
    13:43:44    authenticator: None
    13:43:44    oauth_client_id: None
    13:43:44    query_tag: john
    13:43:44    client_session_keep_alive: False
    13:43:44    host: None
    13:43:44    port: None
    13:43:44    proxy_host: None
    13:43:44    proxy_port: None
    13:43:44    protocol: None
    13:43:44    connect_retries: 0
    13:43:44    connect_timeout: 10
    13:43:44    retry_on_database_errors: False
    13:43:44    retry_all: False
    13:43:44    insecure_mode: False
    13:43:44    reuse_connections: True
    13:43:44  Registered adapter: snowflake=1.8.4
    13:43:50    Connection test: [OK connection ok]

    13:43:50  All checks passed!
    ```


You're good to go!


# 📚 Other helpful resources for learning!

### dbt docs
- [models](https://docs.getdbt.com/docs/build/sql-models)
- [tests](https://docs.getdbt.com/docs/build/data-tests)
- [sources](https://docs.getdbt.com/docs/build/sources)
- [seeds](https://docs.getdbt.com/docs/build/seeds)
- [snapshots](https://docs.getdbt.com/docs/build/snapshots)
- [dbt_project.yml](https://docs.getdbt.com/reference/dbt_project.yml)
- [profiles,yml](https://docs.getdbt.com/docs/core/connect-data-platform/profiles.yml)
- [Commands](https://docs.getdbt.com/reference/commands/build)
- [Node selection](https://docs.getdbt.com/reference/node-selection/syntax)

### 📂 Navigating the Repository

Each dbt project contains various directories and files. Learn more about the structure of the project below:

- **`dbt_packages/`**: This folder is where dbt install packages (outside projects).
- **`logs/`**: This folder is where dbt store logs.
- **`macros/`**: This folder is where dbt searches for custom macros.
- **`models/`**: This folder is where dbt searches for models. You can create subfolders in the way you want, no problem.
- **`seeds/`**: This folder is where dbt searches for seeds.
- **`snapshots/`**: This folder is where dbt searches for snapshots.
- **`target/`**: This folder is where dbt stores [artifacts](https://docs.getdbt.com/reference/artifacts/dbt-artifacts) and the compiled SQL code (the code dbt sends to the data warehouse to run).
- **`tests/`**: This folder is where dbt searches for custom tests (generic or singular).
- **`dbt_project.yml`**: Every dbt project needs a dbt_project.yml file — this is how dbt knows a directory is a dbt project. It also contains important information that tells dbt how to operate your project. [More info here](https://docs.getdbt.com/reference/dbt_project.yml).
- **`packages.yml`**: This folder is where you define the packages you want dbt to install.