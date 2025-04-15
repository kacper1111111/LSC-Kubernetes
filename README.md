# LSC-Kubernetes

## 1. Add NFS server provisioner helm repository
```bash
helm repo add nfs-server-provisioner https://kvaps.github.io/charts

helm repo update
```

## 2.	Installation of the NFS server with helm
```bash
helm install nfs-provisioner nfs-server-provisioner/nfs-server-provisioner -f nfs-helm-values.yaml
```

## 3. Create Persistent Volume Claim (PVC)
```bash
kubectl apply -f persistent-volume-claim.yaml
```

## 4. Deploy the Nginx web server
```bash
kubectl apply -f webserver-deployment.yaml
```

## 5. Create the service
```bash
kubectl apply -f webserver-service.yaml
```

## 6. Inject initial web content
```bash
kubectl apply -f content-injector-job.yaml
```

## 7. Check deployment status
```bash
kubectl get pods
```

## 8. Some checks
- Check the status of the PVC
```bash
kubectl get pvc webapp-content-pvc
```

- Check the status of the Nginx deployment
```bash
kubectl get deployment webserver-app
```

- Check the status of the content injection job
```bash
kubectl get job content-injector
```

- Check the service and find the External IP or Hostname for the Load Balancer
```bash
kubectl get svc webapp-service
```
