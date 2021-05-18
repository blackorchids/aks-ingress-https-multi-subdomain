

## Steps ##
1) generate self-sign-certificate
   - openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 10000 -nodes
2) Access AKS with Azure cloud shell **(If you access to AKS private Cluster you need to access from VM that is located in the same AKS Cluster Network)**
   - az account set --subscription [Subscription ID]
   - az aks get-credentials --resource-group [RG-Name] --name [aks cluster name]
3) Create Secret in AKS
   - kubectl create secret tls [secret name] --key [key name (key.pem)] --cert [cert name (cert.pem)]
4) Apply workload, service and ingress to AKS cluster
   - kubectl apply -f [yaml]
5) Verify workload deployment
   - kubectl get pod,service,ingress
6) Notice listeners, backend in Application Gateway
