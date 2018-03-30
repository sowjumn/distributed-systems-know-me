# Kubernetes Installation guidelines 

To Run Kubernetes locally you will need to do the following

1. Install a hypervisor:
Before you install Minikube you will need a VM driver. You could use any driver from the list of drivers in [this](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md) document. But its recommended to use Hyperkit.

2. Install kubectl with homebrew:
`brew install kubectl`
`kubectl version`

3. Install Minikube:
Follow the Minikube installation instructions [here](https://github.com/kubernetes/minikube/releases)

4. Set the Minikube context: 
The context is what determines which cluster kubectl is interacting with. You can see all your available contexts in the ~/.kube/config file.
`kubectl config use-context minikube`

5. Verify that kubectl is configured to communicate with your cluster:
`kubectl cluster-info`

6. Reusing the Docker Daemon of Minikube:
When using a single VM of Kubernetes, it’s really handy to reuse the minikube’s built-in Docker daemon; as this means you don’t have to build a docker registry on your host machine and push the image into it - you can just build inside the same docker daemon as minikube which speeds up local experiments. 
`eval $(minikube docker-env)`

7. Deploy a node app on to a kubernetes pod
https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/#create-your-nodejs-application
