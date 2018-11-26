# SimpleKubeCluster
A simple cluster using minikube for deploying local applications
For deploying a simeple local cluster for developing/testing applications, start with the following steps
## Install minikube
1. brew cask install minikube
2. brew install kubernetes-cli

## Start minikube
1. minikube start (takes a couple of mins)
2. minikube ip (to get the ip of the node)
3. minikube dashboard (opens the kubernetes dashboard in a browser)

## Create config map for nginx.conf file
1. kubectl create configmap nginx-conf --from-file=nginx.conf
2. kubectl get configmaps (verify config map was created)

## Create deployment using nginx.yaml file
1. kubectl apply -f nginx.yaml
2. kubectl get pods (Verify 2 nginx pods are created)

## Expose nginx deployment to be available on 8080
1. kubectl expose deployment nginx-deployment --type=NodePort --port=8080 --target-port=8080
2. curl $(minikube service nginx-deployment --url) (Verify nginx home page is seen)
3. echo $(minikube service nginx-deployment --url)
4. <URL-FROM-STEP-3>/hello/ - should return hello world in json format
