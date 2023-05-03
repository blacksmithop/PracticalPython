# ❓ Why use containers

Before Docker was a thing microservices were deployed using Virtualization. Individual VM's were used to run each service and as you can see it is a huge waste of resources.

We had this host Operating System on top of which sit a Hypervisor. We run our VM's on top of this.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

As you can see each VM needs an Operating System as well libraries to function. When you have multiple VMs this adds up to a lot of resources.



With Containers resource sharing is much more flexible and ununsed resources are shared among the other containers.
