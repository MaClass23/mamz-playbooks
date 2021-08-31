####################################################################################################

Write a Dockerfile that scrapes a website of your choosing.


Your task is as follows:


Create a Dockerfile that spins up a database.
Create another Dockerfile.
When run will scrape some information from a website of your choosing (it can be any information).
It will store that information in the database running in the other docker container
Create the YAML files required for deploying
Write an Ansible playbook for installing Docker, Minikube, and kubectl that creates a deployment in minikube with all of the containers running
Describe how you would test such an application
Describe potential flaws in the design and how you could fix them
###############################################################################################

Setup overview
###############
We will be setting up a Kubernetes cluster that will consist of one master and two worker nodes. All the nodes will run Ubuntu Xenial 64-bit OS and Ansible playbooks will be used for provisioning.

Step 1: Creating a Vagrantfile 
Use the text editor of your choice and create a file with named Vagrantfile, inserting the code below. The value of N denotes the number of nodes present in the cluster, it can be modified accordingly. In the below example, we are setting the value of N as 2.

Step 2: Create an Ansible playbook for Kubernetes master.
Create a directory named kubernetes-setup in the same directory as the Vagrantfile. Create two files named master-playbook.yml and node-playbook.yml in the directory kubernetes-setup.

In the file master-playbook.yml, add the code below.

Step 2.1: Install Docker and its dependent components.
We will be installing the following packages, and then adding a user named “vagrant” to the “docker” group.

docker-ce
docker-ce-cli
containerd.io

Step 2.2: Kubelet will not start if the system has swap enabled, so we are disabling swap using the below code. 
Step 2.3: Installing kubelet, kubeadm and kubectl using the below code.
Step 2.3: Initialize the Kubernetes cluster with kubeadm using the below code (applicable only on master node).
Step 2.4: Setup the kube config file for the vagrant user to access the Kubernetes cluster using the below code
Step 2.5: Setup the container networking provider and the network policy engine using the below code.
Step 2.6: Generate kube join command for joining the node to the Kubernetes cluster and store the command in the file named join-command.
Step 2.7: Setup a handler for checking Docker daemon using the below code.
Step 3: Create the Ansible playbook for Kubernetes node.
Create a file named node-playbook.yml in the directory kubernetes-setup.

Add the code below into node-playbook.yml

Step 3.1: Start adding the code from Steps 2.1 till 2.3.
Step 3.2: Join the nodes to the Kubernetes cluster using below code.

