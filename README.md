# task-3
Create an EKS Cluster:
Log into the AWS Management Console.
Go to EKS and click on Create Cluster.
Choose the region, for example, us-west-2.
Set a name for the cluster, for example, microservices-cluster.
Choose the Kubernetes version you want to use (latest recommended).
Set up a VPC or use an existing one (EKS requires a VPC with specific settings).
Add worker nodes:
Choose EC2 instances for worker nodes.
Pick an instance type, e.g., t3.medium for testing.
Set the Node IAM role (if not already created, create one with necessary EKS permissions).
Click Create Cluster and wait until it is fully created.
Commands to AWS CLI and kubectl on your local machine
   aws eks --region us-west-2 update-kubeconfig --name microservices-cluster
   kubectl get nodes
auth-service-deployment.yaml
user-service-deployment.yaml
order-service-deployment.yaml
microservices-ingress.yaml
Commands to Create Secrets for Environment Variables:
  kubectl create secret generic auth-service-secrets --from-literal=database-url='your-database-url'
  kubectl create secret generic user-service-secrets --from-literal=database-url='your-database-url'
  kubectl create secret generic order-service-secrets --from-literal=database-url='your-database-url'
Commands to Apply the YAML Files:
  kubectl apply -f auth-service-deployment.yaml
  kubectl apply -f user-service-deployment.yaml
  kubectl apply -f order-service-deployment.yaml
  kubectl apply -f microservices-ingress.yaml
Commands to Verify the Deployments:
  kubectl get deployments
  kubectl get pods
  kubectl get services
  kubectl get ingress
To get the external IP of the service, run:
  kubectl get svc

  



