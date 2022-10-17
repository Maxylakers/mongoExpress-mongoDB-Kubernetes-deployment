This is a simple Browser request flow through Kubernetes components

The Setup is created using Kubernetes configuration files

- Here, a request comes in through the Browser aim for the Mongo Express Application/Pod and goes through the external service to the Mongo Express Pod, then goes through the the internal service connecting the Mongo Express Pod and the Mongo DB database Pod which verifying its DB user and DB pwd credentials through the Secrets.

- Note: the create configuration in mongo-secret.yaml should be applied first before that deployment
- Note: Also, to create the configMap, the configuration in mongo-configmap.yml has to be applied first before that of the mongo-express deployment


- After applying all service and deployments, you will find that the "loadbalancer" type of service will have have its status set to pending. To expose this, you will have to pass the command: minikube service mongo-express-service