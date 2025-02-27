# Gcloud commands

`gcloud GROUP SUB-GROUP ACTION`

## Basic configuration

```Shell
# Initialize glcoud
gcloud init

# List gcloud configuration
gcloud config list
gclous config list --all
gcloud config list compute/region
gcloud config list compute/region

# Multiple configurations
gcloud config configurations create/delete/describe/activate/list <CONFIG_NAME>
gcloud config configurations activate <CONFIG_NAME>

# List gcloud account
gcloud config list account
gcloud config list core/account

# Set 
gcloud config set core/project <PROJECT-ID>
gcloud config set compute/region <REGION>
gcloud config set compute/zone <ZONE>

# List regions, zones
gcloud compute zones list
gcloud compute regions list
gcloud compute machine-types list --filter zone:europe-west1-b
```

## Create VM instances

```Shell
gcloud compute instance create <VM_NAME> --machine-type=e2-micro
gcloud compute instance delete <VM_NAME> --zone=europe-west1-b

gcloud compute instance-templates list
gcloud compute instances create test2-from-template \
--source-instance-template=https://www.googleapis.com/compute/v1/projects/tensile-talent-448510-a8/regions/europe-west1/instanceTemplates/instance-template-20250225-111311  --zone=europe-west1-c
```

## APP ENGINE

IAM roles:

- App Engine Admin
- Storage Admin
- Artifact Registry Writer
- Artifact Registry Create-on-Push Writer
- Logs Writer

```Shell
gcloud config set project <PROJECT_NAME>
gcloud app create

# Deploying
gcloud app deploy main.yaml --version=v3 --no-promote --stop-previous-version
gcloud app deploy --image-url eu.gcr.io/<PROJECT_ID>/hello-rest-api:0.0.0.RELEASE

# Listing
gcloud app services list
gcloud app instances list
gcloud app versions list --hide-no-traffic

# Browseing
gcloud app browse --service="myservice"
gcloud app browse --version=v3

# Logs
gcloud app opens-console --logs
gcloud app logs tail

# Services
gcloud app services browse/delete/describe/list/set-traffic

# Versions
gcloud app versions browse/delete/describe/list/migrate/start/stop
gcloud app versions migrate v2 --versions="v3"

# Instances
gcloud app instances delete --service=s1 --version=v1
gcloud app instances describe
gcloud app instances list
```

## GKE - Google Cloud Kubernetes Engine

```Shell
gcloud config list
gcloud config set core/disable_usage_reporting true

# Register kubctl
gcloud container clusters create get-credentials my-gke-cluster --zone=europe-west1-c

# Crate a cluster
gcloud container clusters create my-gke-cluster --zone=europe-west1-c

# Create deployment
kubectl create deployment first-deployment --image=nginx:latest
kubectl get deployment
kubectl get nodes
kubectl get pods

# Manual scaling
## Pods
kubectl scale deployment deployment-1 --replicas=2
kubectl get podsg
## Nodes
cloud container clusters resize my-gke-cluster --node-pool=default-pool --num-nodes=2 --zone=europe-west1-c
kubectl get nodes
# Expose deployment
kubectl expose deployment deployment-1 --type=LoadBalancer --port=8080 --target-port=80

# Auto scalinig
# Pods
kubectl autoscale deployment deployment-1 --max=4 --cpu-percent=70
kubectl get hpa
kubectl get pods

# Config map
kubectl get configmap
kubectl get secret
kubectl get service

# Delete
## Service
kubectl delete service deployment-1-service
## Deployment
kubectl delete deployment deployment-1
## Cluster
gcloud container clusters list
gcloud container clusters delete my-gke-cluster --zone=europe-west1-c
```
