This is a simple Browser request flow through Kubernetes components

The Setup is created using Kubernetes configuration files

- Here, a request comes in through the Browser aim for the Mongo Express Application/Pod and goes through the external service to the Mongo Express Pod, then goes through the the internal service connecting the Mongo Express Pod and the Mongo DB database Pod which verifying its DB user and DB pwd credentials through the Secrets.

- Note: the create configuration in mongo-secret.yaml should be applied first before that deployment
- Note: Also, to create the configMap, the configuration in mongo-configmap.yml has to be applied first before that of the mongo-express deployment


- After applying all service and deployments, you will find that the "loadbalancer" type of service will  have its status set to pending. To expose this, you will have to pass the command: minikube service mongo-express-service (that is if you have selected the minikube driver type to be virtual box or hyper V)

- On the other hand, if you had choosen docker as the driver type, you could use port forwarding on a new terminal using the command: kubectl port-forward service/mongo-express-service 30000:8081

- This wy you would be able to access the local cluster via its external service using the address: http://127.0.0.1:30000 as seen below, and in the screenshorts folder.

<img width="940" alt="Express-landing-page" src="https://user-images.githubusercontent.com/47093323/197525605-90825402-8662-41b7-be36-a610400619dd.PNG">

<img width="895" alt="db-collection-page" src="https://user-images.githubusercontent.com/47093323/197526029-1914548b-a5a5-4d9b-9c6a-6d53fe3eeef1.PNG">