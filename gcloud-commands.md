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
gcloud config set core/disable_usage_reporting true

# List regions, zones
gcloud compute zones list
gcloud compute regions list
gcloud compute machine-types list --filter zone:europe-west1-b
```

## Projects

```Shell
gcloud projects create/delete/describe/list
gcloud add-iam-policy binding #  Adds a single IAM policy binding (i.e., grants a role to a user, group, or service account) without affecting existing bindings.
gcloud projects add-iam-policy-binding PROJECT_ID \
    --member="user:example@example.com" \
    --role="roles/viewer"

gcloud set-iam-policy # Purpose: Replaces the entire IAM policy for a resource with a new policy (modifying, adding, or removing bindings).
gcloud projects get-iam-policy PROJECT_ID > policy.json
# Edit policy.json manually
gcloud projects set-iam-policy PROJECT_ID policy.json
```

## Create VM instances

```Shell
gcloud compute instance create <VM_NAME> --machine-type=e2-micro
gcloud compute instance delete <VM_NAME> --zone=europe-west1-b

gcloud compute instance-templates list
gcloud compute instances create test2-from-template \
--source-instance-template=https://www.googleapis.com/compute/v1/projects/tensile-talent-448510-a8/regions/europe-west1/instanceTemplates/instance-template-20250225-111311  --zone=europe-west1-c
```

## APP engine

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
### Manage Cluster
# Create a cluster
gcloud container clusters create my-gke-cluster --zone=europe-west1-b --node-locations=europe-west1-b --disk-size=10G

# Resize a cluster
gcloud container clusters resize my-gke-cluster --node-pool=default-pool --num-nodes=2 --zone=europe-west1-b

# Autoscale cluster
gcloud container clusters update my-gke-cluster --enable-autoscaling --min-nodes=1 --max-nodes=3

# Adding node pool
gcloud container node-pools create new-node-pool --cluster my-gke-cluster

# Delete cluster
gcloud container clusters list
gcloud container clusters delete my-gke-cluster --zone=europe-west1-b

# Images - Gcloud container registry
gcloud container images list

# Create Sub-network
gcloud container clusters create --create-subnetwork name=my-subnet,range=/21

### Manage deployment
# Register kubctl
gcloud container clusters get-credentials my-gke-cluster --zone=europe-west1-b

# Create deployment
kubectl create deployment first-deployment --image=nginx:latest
kubectl apply -f deployment.yaml
kubectl get deployment
kubectl describe deployment deployment-1
kubectl get nodes
kubectl get pods

# Manual scaling
kubectl scale deployment deployment-1 --replicas=2

# Expose deployment
kubectl expose deployment deployment-1 --type=LoadBalancer --port=8080 --target-port=80

# Auto scalinig
kubectl autoscale deployment deployment-1 --max=4 --cpu-percent=70
kubectl get hpa
kubectl get pods
kubectl get replicaset

# Config map
kubectl get configmap
kubectl get secret
kubectl get service

# Rollback
kubectl rollout undo deployment hello-world --to-revision=1

# Delete
kubectl delete service deployment-1-service
kubectl delete deployment deployment-1
```

## Storage

```Shell
# Change Storage Class
gcloud storage objects update gs://BUCKET_NAME/OBJECT_NAME --storage-class=STORAGE_CLASS

# Assign IAM role
gsutil iam ch user:(user_email):(role1,role2) gs://(BUCKET)

# Remove IAM role
gsutil iam ch -d user:(user_email):(role1,role2) gs://(BUCKET)

# Assign ACLs
gsutil acl ch -u (user_email):(O/R/W) gs://(BUCKET)

# Delete all ACLs
gsutil acl ch -d (user_email) gs://(BUCKET)

# Signed URLs
gsutil signurl -d (time_period (10m)) (keyfile.json) gs://(BUCKET)/(object)

# Versioning policy
gsutil versioning get gs://BUCKET
gsutil versioning set on gs://BUCKET
gsutil ls -a gs://BUCKET

# Lifecycle policy
gsutil lifecycle get gs://BUCKET > filename.json
gsutil lifecycle set filename.json gs://BUCKET
```
