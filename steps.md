On your local machine

1. Install Git bash
2. Install docker Desktop and in gitbash run below command
       --> Docker --version
       --> docker ps
       if this give error, like error response from daemon: desktop is unable to start, T-shoot with the help of google, you can do it.

3. Install kubectl

https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

4. Install Kind, steps mentioned here

 https://kind.sigs.k8s.io/docs/user/quick-start/#installation

 
5. create a kind_config.yml

6. kind create cluster --config kind_config.yml

it may give error docker pull image failed something

so run

docker login

kind create cluster --config kind_config.yml

kubectl cluster-info --context kind-my-first-cluster

