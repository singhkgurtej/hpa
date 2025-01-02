Hi, In this tutorial we will try to understand how a Horizontal Pod Autoscaler works in Kubernetes.

As the name says a Horizontal Pod Autoscaler scales the number of pods up or down depending on the resource utilization. 
We can define the maximum and minimum number of replicas for the respective target. Now say you defined the minimum number as 1 and maximum replicas as 10, does HPA scale to 10 every time the resource limit is breached?
Not exactly, the HPA algorithm decides the number of replicas to scale to using the following formula"

desiredReplicas = ceil[currentReplicas * ( currentMetricValue / desiredMetricValue )]

Lets do a quick demo of Horizontal Pod Autoscaler

Steps:
1. Create a local kubernetes cluster using kind
   kind create cluster --config kind-cluster-1.yaml
2. Deploy the K8s manifests. This should create a deployment and a service
3. Depoloy thye metric server
4. Deploy HPA
5. Pump up the load 
6. Watch the HPA do its magic

