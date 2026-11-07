# CI/CD Final Project: Automation, Tekton & OpenShift Pipelines

## Project Name: Account Service CI/CD Pipeline

This repository implements an automated Continuous Integration and Continuous Deployment (CI/CD) pipeline for the **Account Service** microservice application using GitHub Actions, Tekton Tasks, and Red Hat OpenShift Pipelines.

---

### Project Structure & Features
- **Automation with GitHub Actions**: `.github/workflows/workflow.yml`
  - Automated dependency setup
  - Python linting using `flake8`
  - Automated unit testing with code coverage using `nosetests`
- **Cloud-Native Tasks with Tekton**: `.tekton/tasks.yml`
  - `cleanup` task for persistent workspace maintenance
  - `nose` test task executing isolated test suites
- **OpenShift Pipelines Integration**:
  - Sequential pipeline run: `cleanup` -> `git-clone` -> `flake8` -> `nose` -> `buildah` -> `openshift-client (deploy)`
  - Persistent volume claim storage using `skills-network-learner` storage class (1GB)
  - Deployment verification serving traffic on port 8000 with log tag `SERVICERUNNING`

