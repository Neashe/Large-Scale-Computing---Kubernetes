# Large Scale Computing - Kubernetes
Labs from LSC course - Computer Science, AGH 

## Requirements
- Kubernetes
- Helm
- Kubernetes cluster created
## Commands (for existing Kubernetes cluster)

```
aws eks --region <your-region> update-kubeconfig --name <your-cluster-name>

helm repo add nfs-ganesha-server-and-external-provisioner https://kubernetes-sigs.github.io/nfs-ganesha-server-and-external-provisioner/
helm install nfs-server-provisioner nfs-ganesha-server-and-external-provisioner/nfs-server-provisioner --set=storageClass.name=mystorageclass

kubectl apply -f pvc.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f job.yaml
```

## Lab instructions
Create a Kubernetes application

a) Create a k8s cluster using Amazon Elastic Kubernetes Service (EKS)  

 - You can also use minikube, kind, or any other Kubernetes distribution, or existing cluster. 

b) Using Helm, install an NFS server and provisioner in the cluster. 

 - Go to charts/nfs-server-provisioner for a README.  

 - Pay attention to configuration parameters, in particular, override storageClass.name which denotes the name of the StorageClass that you’ll have to use when creating Persistent Volume Claims.  

c) Create a Persistent Volume Claim which will bind to a NFS Persistent Volume provisioned dynamically by the provisioner installed in the previous step.  

d) Create a Deployment with a HTTP server (e.g., apache or nginx). The web content directory should be mounted as a volume using the PVC created in the previous step.  

e) Create a Service associated with the Pod(s) of the HTTP server Deployment. 

f) Create a Job which mounts the PVC and copies a sample content through the shared NFS PV. 

g) Test the HTTP server by showing the sample web content in a browser.  


