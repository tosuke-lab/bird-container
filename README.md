# BIRD for PureLB

PureLB is a load-balancer orchestrator for Kubernetes clusters.  It uses standardLinux networking and routing protocols,  and works with the operating
system to announce service addresses

This is a simple packaging of the open source routing software [BIRD](https://bird.network.cz) Version 2.0 (currently 2.0.7)


The included sample configuration bird-cm.yml imports the routing table entries created when PureLB adds allocated load-balancer addresses to kube-lb0


## Documentation

The PureLB documentation describes use alongside PureLB.

https://purelb.gitlab.io/docs


## Quick Start


* Edit the Bird configmap to enable & configure routing

* Create the router namespace<br/>
`kubectl create namespace router`
* Apply the edited configmap<br/>
`kubectl apply -f bird-cm.yml`
* Deploy the Bird Router<br/>
`kubectl apply -f bird.yml`

Note that the binaries of bird are not located in the directory.  BIRD
needs to be built on the OS used by the container.  The dockerfile
assumes that you have built BIRD on an OS matching the FROM ubuntu label 
and copied the binaries into the dockerfile directory before creating.  Only two bird binaries are required, bird and birdc.  Built from BIRD 2.0.7
