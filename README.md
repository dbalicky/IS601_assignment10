# Setup

## Set python version to 3.10.11
```bash
pyenv local 3.10.11
```

## Create and activate venv
```bash
python3 -m venv venv
source venv/bin/activate
```

## Install dependencies from requirements.txt
```bash
pip install -r requirements.txt
```

## Upgrade pip
```bash
pip install --upgrade pip
```

## Updating requirements.txt version installs
```bash
pip install --upgrade -r requirements.txt
```

## Initialize and connect to GitHub
```bash
git init
```

```bash
git remote set-url origin git@github.com:dbalicky/IS601_assignment10.git
# or git remote add origin git@github.com:dbalicky/IS601_assignment10.git
```
## Connect to pgadmin
```bash
docker compose up -d
...
...
...
 ✔ Image assignment10-web           Built                                                                       176.3s
 ✔ Volume assignment10_pgadmin_data Created                                                                       0.0s
 ✔ Container postgres_db            Healthy                                                                       5.2s
 ✔ Container fastapi_calculator     Started                                                                       5.2s
 ✔ Container pgadmin                Started                                                                       5.6s
```
Go to pgadmin and log in

# Issues

## Pytest errors

All tests fail, 1 skipped, 74 errors
```bash
qlalchemy.exc.OperationalError: (psycopg2.OperationalError) connection to server at "localhost" (127.0.0.1), por...
```

Change postgres version to 17 in docker-compose.yml:
```bash
image: postgres:17
```

Then recreate PostgreSQL Docker setup:
```bash
docker compose down -v
docker compose up -d db
```
# Testing 

```bash
pytest -s -v <test> --preserve-db
```

**-s**
Disables output capture so terminal and print() outputs show immediately

**-v**
Shows full name and output of each test

**--preserve-db**
Preserves database for test instead of deleting and recreating it