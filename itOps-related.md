# just links w/some notes 

- https://medium.com/@tomglenn91/kubernetes-for-dummies-by-a-dummy-80b67c00214
- https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0
- https://medium.com/free-code-camp/learn-kubernetes-in-under-3-hours-a-detailed-guide-to-orchestrating-containers-114ff420e882
  - > After we started our Microservices from containers we had one question, let’s elaborate it further in a Q&A format:
Q: How do we scale containers?
A: We spin up another one.
Q: How do we share the load between them? What if the Server is already used to the maximum and we need another server for our container? How do we calculate the best hardware utilization?
A: Ahm… Ermm… (Let me google).
Q: Rolling out updates without breaking anything? And if we do, how can we go back to the working version.
  - > Kubernetes solves all these questions (and more!). My attempt to reduce Kubernetes in one sentence would be: “Kubernetes is a Container Orchestrator, that abstracts the underlying infrastructure. (Where the containers are run)”.
- 


## some practice 

- https://www.windowscentral.com/how-check-your-computer-uptime-windows-10
	
> wmic path Win32_OperatingSystem get LastBootUpTime

For example, the LastBootUpTime 20181219104602.500000-300 can be broken down using the info below.
	Year: 2018.
	Month: 12.
	Day: 19.
	Hour: 10.
	Minutes: 46.
	Seconds: 02.
	Milliseconds: 500000.
	GMT: -300 (5 hours ahead of GMT).
	
> systeminfo | find "System Boot Time"

C:\Users>systeminfo | find "System Boot Time"
  System Boot Time:          24/09/2021, 20:01:11	
```
