## Kubernetes Commands

### Get Pods
`kubectl get pods`

### Connect to Jmeter master
`kubectl exec -ti jmeter-master-dp6jc -- /bin/bash`

### Get IP Address of Pod
`kubectl describe pods fcrepo-activemq | grep IP`

### Kubernetes Cheatsheet
https://kubernetes.io/docs/user-guide/kubectl-cheatsheet/