# Monitoring With Prometheus and Grafana
## Step 1: Install Helm Chart on Ubuntu Server
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
```
```
chmod 700 get_helm.sh
```
```
./get_helm.sh
 DESIRED_VERSION=v3.8.2 bash get_helm.sh
 curl -L https://git.io/get_helm.sh | bash -s -- --version v3.8.2
```
```
helm version
```
## Step 2: Add Helm Stable Charts for Your Local Client
```
helm repo add stable https://charts.helm.sh/stable
```
## Step 3: Add Prometheus Helm Repository
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
## Step 4: Create Prometheus Namespace
```
kubectl create namespace prometheus
```
```
kubectl get ns
```
## Step 5: Install Prometheus using Helm
```
helm install stable prometheus-community/kube-prometheus-stack -n prometheus
```
```
kubectl get pods -n prometheus
```
```
kubectl get svc -n prometheus
```
## Step 6: Expose Prometheus and Grafana to the external world edit the ClusterIP to LoadBalancer
```
kubectl edit svc stable-kube-prometheus-sta-prometheus -n prometheus
```
```
kubectl get svc -n prometheus
```
## Step 6: Edit SVC file Grafana
```
kubectl edit svc stable-grafana -n prometheus
```
```
kubectl get svc -n prometheus
```
## Step 6: Decode Grafana Password
```
l get secret --namespace prometheus stable-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
<img width="1365" height="678" alt="grafana password access" src="https://github.com/user-attachments/assets/67689a2d-c78e-4784-9b27-bc2f8285f006" />

<img width="1364" height="674" alt="access prometheus through load balancer" src="https://github.com/user-attachments/assets/17f60508-8c24-4d80-a5cf-18e3c56e046d" />

<img width="1364" height="682" alt="grafana main dashboard 1" src="https://github.com/user-attachments/assets/b70a0e16-c65b-40b2-8774-631ba3dd1c76" />

<img width="1365" height="674" alt="grafana dashboard 4" src="https://github.com/user-attachments/assets/52e757c4-10e8-4342-a028-d3d8a6e11120" />

<img width="1363" height="672" alt="grafana dashboard 3" src="https://github.com/user-attachments/assets/5ae13dcc-6259-465a-b815-85e8664a4f69" />

<img width="914" height="270" alt="e-commerce pods" src="https://github.com/user-attachments/assets/7656f66d-e236-49e3-99ec-c8fd312afa30" />

<img width="1364" height="519" alt="ecommerce service" src="https://github.com/user-attachments/assets/2dd7d9fc-c7a8-4d16-bd0a-d03d8346fd6a" />




