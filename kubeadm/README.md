## kubeadm config
For the kubeadm config I created a config file.
I wanted to use containerd runtime and my server also has docker runtime, I needed to specify the CRI socket.
I also specified that k8s should not use swap. I disabled the swap on my server to avoid any issue.
Kubernetes seems to work pretty badly with swap.
