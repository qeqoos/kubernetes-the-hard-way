# Provisioning Compute Resources

Ubuntu 18.04

2 controllers (2 units each)
2 nodes (2 units each)
1 kube API loadbalancer (1 unit)

1 unit = 1vCPU, 1GB RAM.

Total 9 units in ACG sandbox.

## Networking

The Kubernetes [networking model](https://kubernetes.io/docs/concepts/cluster-administration/networking/#kubernetes-model) assumes a flat network in which containers and nodes can communicate with each other. In cases where this is not desired [network policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) can limit how groups of containers are allowed to communicate with each other and external network endpoints.

> Setting up network policies is out of scope for this tutorial.

## Compute Instances

The compute instances in this lab will be provisioned using [Ubuntu Server](https://www.ubuntu.com/server) 18.04, which has good support for the [containerd container runtime](https://github.com/containerd/containerd). Each compute instance will be provisioned with a fixed private IP address to simplify the Kubernetes bootstrapping process.

## Configuring SSH Access

SSH will be used to configure the controller and worker instances. Add SSH keys to all servers.

```
ssh-keygen
ssh-copy-id <user>@<ip>
```

After the SSH keys have been updated you'll be logged into the instance:

```
Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 5.4.0-1042-gcp x86_64)
...
```

Type `exit` at the prompt to exit the compute instance:

```
$USER@$HOSTNAME:~$ exit
```
> output

```
Connection to XX.XX.XX.XXX closed
```

Next: [Provisioning a CA and Generating TLS Certificates](04-certificate-authority.md)
