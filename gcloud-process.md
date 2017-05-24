## Google Cloud Distributed Testing process

### Build Test Subject Image
`docker build -t pandorasystems/fcrepo .`

### Tag Image
`docker tag pandorasystems/fcrepo eu.gcr.io/pandora-framework/fcrepo`

### Push Image
`gcloud docker -- push eu.gcr.io/pandora-framework/fcrepo`

### Build Cluster
`gcloud container --project "pandora-framework" clusters create "cluster-1" --zone "europe-west1-b" --machine-type "n1-standard-1" --image-type "COS" --disk-size "100" --scopes "https://www.googleapis.com/auth/compute","https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring.write","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --num-nodes "3" --network "default" --enable-cloud-logging --enable-cloud-monitoring`

### Connect to Cluster
`gcloud container clusters get-credentials cluster-1 \
    --zone europe-west1-b --project pandora-framework` 
 
### Deploy Images
`kubectl create -f ./kubernetes`

### Get IP addresses of jmeter workers
`kubectl describe pods --selector=role=worker | grep IP`

### Get IP address of fcrepo pod
`kubectl describe pods fcrepo-activemq | grep IP`

### Connect to jmeter Master
`kubectl exec -ti jmeter-master-dp6jc -- /bin/bash`

### Build and Run jmeter Command
`./jmeter -Gfedora_4_server=10.0.1.5 -Gfedora_4_context=fcrepo/rest -Gcontainer_threads=1 -l perf.log -n -t fedora-new.jmx -R10.0.1.6,10.0.1.7,10.0.0.6,10.0.2.5,10.0.0.7`

### Get Results
`kubectl cp jmeter-master-dp6jc:/opt/apache-jmeter-3.2/bin/perf.log /tmp/perf.log`

`kubectl cp jmeter-master-dp6jc:/opt/apache-jmeter-3.2/bin/jmeter.log /tmp/jmeter.log`

### Delete Cluster
`gcloud container clusters delete "cluster-1"`