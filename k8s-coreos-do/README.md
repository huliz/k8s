# kubernetes coreos cluster on digitalocean

### kubernetes master with local etcd and docker registry and kubernetes nodes on flannel network

Use the master.yaml config file for the user data and don't forget to enable private networking (and remember the choice of the region and zone)

Wait until the master droplet is UP and note down the Private IP. 

Use the node.yaml for the node droplets.
Replace <master-ip-addr> with the Private IP of the master server and create as many droplets as you would like.
Don't forget to use the same region and zone otherwise your servers will not communicate to each other.

#### monitoring

Before and while creating the nodes, it is useful to ssh into the master droplet and run 
```
fleetctl list-machines
```

### usage

You will need a kubernetes client binary kubectl. Please, refer to the official documentation.
To enable the location of kubernetes master, use the following (replace <master-public-ip-addr> with the Public IP address of the master droplet:
```
export KUBEBERNETES_MASTER=http://<master-public-ip-addr>:8080
```
After that follow the typical guestbook example in the official guide.

You can also set up API server to listen on the local ipv4, if you wish. 
This configuration is for testing purposes and to enable you to quickly start as the official getting-started CoreOS guide does not work on DigitalOcean.

