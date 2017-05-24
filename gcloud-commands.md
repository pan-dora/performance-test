## Build Cluster
`gcloud container --project "pandora-framework" clusters create "cluster-1" --zone "europe-west1-b" --machine-type "n1-standard-1" --image-type "COS" --disk-size "100" --scopes "https://www.googleapis.com/auth/compute","https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring.write","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --num-nodes "3" --network "default" --enable-cloud-logging --enable-cloud-monitoring`

## Connect to Cluster
`gcloud container clusters get-credentials cluster-1 \
    --zone europe-west1-b --project pandora-framework`
    
## Open Kubernetes
`kubectl proxy` @ http://localhost:8001/ui
