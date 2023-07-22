INSTALLATION OF KUBERENETS EKS CLUSTER:
----------------------------------------
* Create a linux instance, install aws cli, create iam credentials
* Aws Cli installation steps:
```
sudo apt update
sudo apt install unzip 
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
aws configure
* Docker installation script:
```
curl -fsSL https://get.docker.com -o install-docker.sh
sh install-docker.sh --dry-run
sudo sh install-docker.sh
``` 
* Kubectl installation steps:
```
curl -LO https://dl.k8s.io/release/v1.27.1/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin 
kubectl version --short --client
```
* Eksctl installation steps:
```
# for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

curl -sLO "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

# (Optional) Verify checksum
curl -sL "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_checksums.txt" | grep $PLATFORM | sha256sum --check

tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo mv /tmp/eksctl /usr/local/bin
```
* Execute ssh-keygen 
* Create a file called as cluster.yaml with the following content
```yaml
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: eks-cluster
  region: ap-south-1

nodeGroups:
  - name: basic
    instanceType: t2.medium
    desiredCapacity: 2
    volumeSize: 20
    ssh:
      allow: true # will use ~/.ssh/id_rsa.pub as the default ssh key
```
* Now execute the command 
```
eksctl create cluster -f cluster.yaml      
```
* After creation execute
```
kubectl get nodes
kubectl get pods --all-namespaces
```
* To delete the EKS clsuter
```
eksctl delete cluster -f cluster.yaml  
```
```
eksctl delete cluster -f cluster.yaml --wait --disable-nodegroup-eviction
```


we can see installed eks and kubctl and helm in this location:  `/usr/local/bin`
