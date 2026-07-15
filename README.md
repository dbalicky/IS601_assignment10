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