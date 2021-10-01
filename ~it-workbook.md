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

https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0

`Ingress {as L7 s/w router} is probably the most powerful way to expose your services, but can also be the most complicated. There are many types of Ingress controllers, from the Google Cloud Load Balancer, Nginx, Contour, Istio, and more. There are also plugins for Ingress controllers, like the cert-manager, that can automatically provision SSL certificates for your services.`

https://medium.com/google-cloud/kubernetes-101-pods-nodes-containers-and-clusters-c1509e409e16

- 

((https://memory-alpha.fandom.com/wiki/Borg)) : “Borg” is the name for the internal Google project Kubernetes was based on. 

# some next item 

.....

// https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax //
