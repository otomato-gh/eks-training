
- Configure the aws cli for your user account and region eu-central-1
```bash
export EKS_USER=<your_user>
export AWS_ACCESS_KEY_ID=YOUR_ACCES_KEY_ID
export AWS_SECRET_ACCESS_KEY=YOUR_SECRET_ACCESS_KEY
export AWS_DEFAULT_REGION=eu-central-1
```
- Create cluster credentials:
```bash
aws eks update-kubeconfig --region eu-central-1  --name training
kubectl config set-context --current --namespace=<your_user>
```
- Verify
```bash
kubectl get all
```
