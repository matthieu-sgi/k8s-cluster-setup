# How to add a node to k8s cluster with containerd container runtime

setup a node with contairnerd container runtime, you have a to install containerd package.
```bash
# For debian based machine
sudo apt install containerd
```

However, you also to have to setup container-cni. Especially for networking.
The method I found to make it work well is to download the setup script from the [containerd repo](https://github.com/containerd/containerd).
You can find it [/script/setup/install-cni.sh](https://github.com/containerd/containerd/blob/main/script/setup/install-cni).
In order to install the CNI you should clone the full repo, you can run :
```bash
git clone https://github.com/containerd/containerd.git
```
However, this script need the go language to be install.
You can follow this [tutorial from go](https://go.dev/doc/install) to install it.
On my side and for my x86 (amd64) node I ran :
```bash
wget https://go.dev/dl/go1.23.6.linux-amd64.tar.gz
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.23.6.linux-amd64.tar.gz
```
You then need to add go to the path.
There are many ways to do. On a debian based machine and for a system wide install you can create a file in `/etc/profile.d/`.
You can create it running this commmand:
```bash
sudo echo -n "export PATH=$PATH:/usr/local/go/bin" > /etc/profile.d/go_bin_path.sh
```
Kubernetes is not working well with swap partition.
I advice you to disable the swap.
For x86 classic machines you can run :
```bash
sudo swapoff -a
```
For raspberry pi and similar units, it is a bit more complicated.
I achieved to do it running:
```bash
sudo dphys-swapfile swapoff
sudo dphys-swapfile uninstall
sudo update-rc.d dphys-swapfile remove
sudo apt purge dphys-swapfile -y
sudo sysctl -w vm.swappiness=0
```
