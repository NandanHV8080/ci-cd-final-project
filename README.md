# CI/CD Final Project: Hit Counter Service

**Course:** IBM CI/CD Tools and Practices (Coursera)  
**Project:** CI/CD for a Python Flask Hit Counter API  
**Repository:** https://github.com/NandanHV8080/ci-cd-final-project

## Overview

This project demonstrates continuous integration with GitHub Actions (flake8 linting and nose unit tests) and continuous delivery with Tekton and OpenShift Pipelines.

The sample Flask service exposes the following endpoints: `/`, `/health`, `/counters`, and `/counters/<name>` (create, read, update, and delete).

## GitHub Actions

The [workflow](.github/workflows/workflow.yml) installs Python 3.9 dependencies, performs lint checks with flake8, runs the test suite with nose, and reports coverage. See the [Actions page](../../actions) for real run results.

## Tekton and OpenShift

The [Tekton tasks](.tekton/tasks.yml) contain workspace cleanup and automated nose test tasks. The complete OpenShift pipeline also needs git-clone, flake8, buildah, and deploy tasks configured in the lab environment.

## Run locally

Use Python 3.9 with the course's pinned dependencies.

```bash
python3.9 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
flake8 service tests --count --show-source --statistics
nosetests -v --with-spec --spec-color
coverage report -m
gunicorn service:app --bind 0.0.0.0:8000
```

## Submission evidence

The final project requires public links to this README, the GitHub Actions workflow, and Tekton tasks, plus real workflow logs, an OpenShift PVC screenshot, pipeline screenshots, and application logs.

## Attribution

Based on the IBM Skills Network CI/CD Tools and Practices final-project starter template. See [LICENSE](LICENSE).
