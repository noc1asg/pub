# kubernetes 101

https://medium.com/@tomglenn91/kubernetes-for-dummies-by-a-dummy-80b67c00214

service.yml : https://gist.github.com/tomdglenn91/46fd1ba1f4f2cb6ae165d7e25a82e26d

deployment.yml : https://gist.github.com/tomdglenn91/8ae2fc55ad1340166f0744c3a10eea61 

command for executing configuration : 

> kubectl apply -f service.yml
 
fetching our public IP (in case of __type: LoadBalancer__) using the following :

> kubectl get service api-service

![diagram](https://miro.medium.com/max/875/1*OA4FgRfYxJ-P2XrGIbbdbg.png)


// https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
