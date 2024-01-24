---
title: "Django Boot-up"
tags: [django, python, web-application-development]
---
# Django Boot-up
## Idea: From Zero to Publicly Available 

## Goals
- Production-ready
- Open-source
- Can run locally
- Accepts payments
- Easily maintainable
- Usable as a template for future projects, to improve "idea to app" "muscle memory"

## "Particulars"
- 3 models, inter-related 
- Payment (Free, Day Pass, Week Pass, Monthly, Annually)

## Assumptions
- Computer / Operating System: MacOS

## Required


## Create new Django project folder
```
django-admin startproject PROJECT_NAME
```

## Python Requirements
requirements.txt
```
# Python libraries here
```

## Process

## Docker
- Install Docker Compose (Mac)
- docker-compose.yaml



- `docker run`: Creates and starts a new Docker container
    - `-it` - Keep the terminal open
    - `--rm` - Delete the container when it exits
    - `-v $PWD:/app` - Mount current working directory ($PWD) into the `/app` directory inside the container
    - `-w /app` -  Sets the working directory inside the container
    - `python:3.8-alpine`- Docker image used for the container
    - `sh -c "pip install django && django-admin startproject myproject" ` -  Install Django

```

docker run \
-it \
--rm \
-v $PWD:/app \
-w /app \
python:3.8-alpine \
sh -c "pip install django && django-admin startproject myproject" 

```




# Make project directory

## Setup Python Environment
```
python3 -m venv venv
source venv/bin/activate
python3 -m pip install --upgrade pip

# Install dependencies
pip install -r requirements.txt
 ```