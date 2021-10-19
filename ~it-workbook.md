# kubernetes 101

## https://medium.com/@tomglenn91/kubernetes-for-dummies-by-a-dummy-80b67c00214

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

## https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0

`Ingress {as L7 s/w router} is probably the most powerful way to expose your services, but can also be the most complicated. There are many types of Ingress controllers, from the Google Cloud Load Balancer, Nginx, Contour, Istio, and more. There are also plugins for Ingress controllers, like the cert-manager, that can automatically provision SSL certificates for your services.`

## https://medium.com/google-cloud/kubernetes-101-pods-nodes-containers-and-clusters-c1509e409e16

((https://memory-alpha.fandom.com/wiki/Borg)) : “Borg” is the name for the internal Google project Kubernetes was based on. 

## https://medium.com/free-code-camp/learn-kubernetes-in-under-3-hours-a-detailed-guide-to-orchestrating-containers-114ff420e882
.....

![fig.14](https://miro.medium.com/max/875/1*8vbHfzW79J2BzpK6X8Tp2g.png)

To summarize, the main properties of Pods are (also shown in figure 14):
1. Each pod has a unique IP address in the Kubernetes cluster
2. Pod can have multiple containers. The containers share the same port space, as such they can communicate via localhost (understandably they cannot use the same port), and communicating with containers of the other pods has to be done in conjunction with the pod ip.
3. Containers in a pod share the same volume(1), same ip, port space, IPC namespace.

(1) Containers have their own isolated filesystems, though they are able to share data using the Kubernetes resource Volumes.

```
> kubectl create -f sa-frontend-pod.yaml 
pod "sa-frontend" created
```

```
> kubectl get pods 
NAME                          READY     STATUS    RESTARTS   AGE
sa-frontend                   1/1       Running   0          7s
```

To access the application externally we create a Kubernetes resource of type **Service**, that will be our next article, which is the proper implementation, but for quick debugging we have another option, and that is port-forwarding:
```
> kubectl port-forward sa-frontend 88:80
Forwarding from 127.0.0.1:88 -> 80
```
```
apiVersion: v1
kind: Pod                                            
metadata:
  name: sa-frontend2      # The only change
spec:                                                
  containers:
    - image: rinormaloku/sentiment-analysis-frontend 
      name: sa-frontend                              
      ports:
        - containerPort: 80
```

Create the new pod by executing the following command:
```
> kubectl create -f sa-frontend-pod2.yaml
pod "sa-frontend2" created
```
**Attention: this is not the final solution, and it has many flaws**. We will improve this in the section for another Kubernetes resource

The Nginx web server with the static files is running inside two different pods. Now we have two questions:
- How do we expose it externally to make it accessible via URL, and
- How do we load balance between them?
Kubernetes provides us the Services resource. Let’s jump right into it, in the next section.

![pods with lables & manifests](https://miro.medium.com/max/875/1*nFNYyevWnLxgpfGSq5X_pg.png)

```
apiVersion: v1
kind: Service              # 1
metadata:
  name: sa-frontend-lb
spec:
  type: LoadBalancer       # 2
  ports:
  - port: 80               # 3
    protocol: TCP          # 4
    targetPort: 80         # 5
  selector:                # 6
    app: sa-frontend       # 7
```
To create the service execute the following command:
```
> kubectl create -f service-sa-frontend-lb.yaml
service "sa-frontend-lb" created
```
You can check out the state of the service by executing the following command:
```
> kubectl get svc
NAME             TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
sa-frontend-lb   LoadBalancer   10.101.244.40   <pending>     80:30708/TCP   7m
```
The External-IP is in pending state (and don’t wait, as it’s not going to change). This is only because we are using Minikube. If we would have executed this in a cloud provider like Azure or GCP, we would get a Public IP, which makes our services worldwide accessible.

Despite that, Minikube doesn’t let us hanging it provides a useful command for local debugging, execute the following command:
```
> minikube service sa-frontend-lb
Opening kubernetes service default/sa-frontend-lb in default browser...
```
This opens your browser pointing to the services IP. After the Service receives the request, it will forward the call to one of the pods (which one doesn’t matter). This abstraction enables us to see and act with the numerous pods as one unit, using the Service as an entry point.



.....

// https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax //
