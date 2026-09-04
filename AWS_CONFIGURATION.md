# AWS Configuration

GitHub Actions deploys the frontend and backend Docker images to Amazon ECR and then applies the Kubernetes manifests to Amazon EKS.

## Repository secrets

Create these four repository secrets in GitHub Settings → Secrets and variables → Actions:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_ACCOUNT_ID`
- `BACKEND_API_URL`

`BACKEND_API_URL` should be the URL of **your own** backend LoadBalancer service after the backend is deployed. Do not use another student's URL.

## Expected AWS resources

The workflows currently use AWS region `us-east-1`, ECR repositories `frontend` and `backend`, and EKS cluster `cluster`. Change those values if your own Terraform environment uses different names.

## Image tagging

Both deployment workflows tag their images with `${GITHUB_SHA}` and deploy that exact image tag through Kustomize. This keeps the deployed image tied to the commit that triggered the workflow.

Never commit AWS credentials to Git.