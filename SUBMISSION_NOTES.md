# Movie Picture Pipeline — Submission Notes

## GitHub Repository

Public repository for this project:

https://github.com/sahithireddy14/automating-simple-cicd

## Required GitHub Actions Workflows

The repository contains the four workflows required by the project:

- `.github/workflows/frontend-ci.yaml` — Frontend Continuous Integration
- `.github/workflows/backend-ci.yaml` — Backend Continuous Integration
- `.github/workflows/frontend-cd.yaml` — Frontend Continuous Deployment
- `.github/workflows/backend-cd.yaml` — Backend Continuous Deployment

## Application URLs

These values must be copied from the live EKS cluster after deployment. Do not use another student's URLs.

### Frontend Service URL

`<PASTE FRONTEND EKS SERVICE URL HERE>`

### Backend Service URL

`<PASTE BACKEND EKS SERVICE URL HERE>`

## Kubernetes Evidence

Run the following command in the Udacity workspace while the EKS cluster is running and capture a screenshot showing the output:

```bash
kubectl get all
```

The screenshot should clearly show the frontend and backend Kubernetes resources and their LoadBalancer services.

## Deployment Verification

Frontend service:

```bash
kubectl get svc frontend
```

Backend service:

```bash
kubectl get svc backend
```

To obtain the LoadBalancer hostnames directly:

```bash
kubectl get svc frontend -o wide
kubectl get svc backend -o wide
```

Use the resulting LoadBalancer hostnames as the Frontend and Backend Application URLs in the Udacity submission.

## GitHub Actions Verification

Before submitting, verify that there is at least one successful run for each of the four workflows. The CI workflows must show successful lint, test, and build jobs. The CD workflows must successfully authenticate to AWS, push the Docker image to ECR, configure the EKS cluster, and deploy the Kubernetes manifests.

## Important

The AWS credentials used by GitHub Actions are stored as repository secrets and are intentionally not included in this file or committed to Git. Required secrets:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

Never commit AWS secret values to the repository.
