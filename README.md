# How to set-up k8s cluster ?

This repo is gathering information on how to setup k8s cluster.
For my first cluster I wanted to use the kubeadm utility. This is not a fully automated set-up and I wanted to understand better on how is it working.

Maybe in a future I will use other way.

## Cluster architecture
This cluster is multi-architecture based and rely on my personnal x86 (amd64) server for the control plane.
For the nodes I have :
 - The control plane server that will be used (x86 based)
 - A raspberry Pi 4 (arm64 based)
