# kubernetes 101

https://medium.com/@tomglenn91/kubernetes-for-dummies-by-a-dummy-80b67c00214

deployment.yml : https://gist.github.com/tomdglenn91/8ae2fc55ad1340166f0744c3a10eea61 

creating pods (with __2 replicas__|instances) :

> kubectl apply -f deployment.yml

service.yml : https://gist.github.com/tomdglenn91/46fd1ba1f4f2cb6ae165d7e25a82e26d

executing configuration (as __api-service__) : 

> kubectl apply -f service.yml

By default, a service is assigned the type of `ClusterIP` 
 
fetching our public IP (as __type: LoadBalancer__) :

> kubectl get service api-service

![diagram](https://miro.medium.com/max/875/1*OA4FgRfYxJ-P2XrGIbbdbg.png)


// https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
