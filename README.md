# Deploy Prometheus Grafana on Minikube (Kubernetes)

## Task 1: Install Minikube on Ubuntu 22.04 VM:

### Install Minikube (use Binary Download):
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64

### Install Docker:
    minikube start --driver=docker
### Basic syntax:
    minikube start/stop/pause
    kubectl create/delete/get
## Task 2: Connect Visual Studio Code (VS code) on Windows to Ubuntu 22.04 VM:
### Download Remote-SSH extension on VS code:
![image](https://github.com/user-attachments/assets/264d419e-0f8c-4287-91d9-818549fbfdfa)
### Get IP and username on Ubuntu 22.04 VM:
- Get IP at ens33:
  -     ip a
![image](https://github.com/user-attachments/assets/5befdba1-60de-4944-8a7c-38b0637c5453)
- Get username:
  -     whoami
![image](https://github.com/user-attachments/assets/c3d79d20-1a43-47f8-8120-e0cc9ef4ecaa)

### Connect Vscode to Ubuntu:
- Use **F1 or Ctrl + Shift + P** to open Command Palette.
![image](https://github.com/user-attachments/assets/3481f14a-66b8-4c7f-a57b-768285ee0bdc)

- Select Remote-SSH: Add New SSH Host...
  - Add remote by use IP and username:
  -     ssh username@IP
  ![image](https://github.com/user-attachments/assets/db72bc85-5f50-40ff-972d-ae8a7efdbd9f)
- Select Remote-SSH: Connect to Host... and connect to remote.
  ![image](https://github.com/user-attachments/assets/38b1a4a4-73a9-44ca-abbb-e593038971a4)
- Check the bottom-left corner of Vs code:  
  ![image](https://github.com/user-attachments/assets/8db539dc-728a-48f5-b900-45e8839a0be3)

## Task 3: Install Kubernetes extension on VS code:
![image](https://github.com/user-attachments/assets/8cb25eec-90ea-4057-9c82-04038b533881)
![image](https://github.com/user-attachments/assets/2e709308-20b7-4f9a-b9cf-419224d7ba4f)

## Task 4: Deploy Prometheus Grafana on the same namespace on Minikube:
- Create namespace:
  -     kubectl create namespace monitoring
### Prometheus:
- create prometheus-config.yaml, prometheus-deployment.yaml, prometheus-service.yaml:
  - [prometheus-config.yaml](https://github.com/locnh8/k8s-monitoring/blob/main/prometheus-config.yaml)
  - [prometheus-deployment.yaml](https://github.com/locnh8/k8s-monitoring/blob/main/prometheus-deployment.yaml)
  - [prometheus-service.yaml](https://github.com/locnh8/k8s-monitoring/blob/main/prometheus-service.yaml)
- Run prometheus using port-forward (**localhost:9090**):
  -     kubectl port-forward service/prometheus-service.yaml 9090:80 -n monitoring
 
### Grafana:
- create grafana.yaml:
  - [grafana.yaml](https://github.com/locnh8/k8s-monitoring/blob/main/grafana.yaml)
- Run grafana using port-forward (**localhost:3000**):
  -     kubectl port-forward service/grafana.yaml 3000:3000 -n monitoring
## OUTPUT:

### Access Prometheus Grafana on browser using kubectl port-forward:
- Grafana (localhost:3000):
![image](https://github.com/user-attachments/assets/e3bd8c33-4a91-49fb-9399-beb93e304d16)
- Prometheus (localhost:9090):
![image](https://github.com/user-attachments/assets/d4cc9ef3-0331-441f-8152-e3b315262ddc)

### Manage Kubernetes resources on VScode:
![image](https://github.com/user-attachments/assets/41bd5124-6539-485e-a0af-ee328cb91f54)
