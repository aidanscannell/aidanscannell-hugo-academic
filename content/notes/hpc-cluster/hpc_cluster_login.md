---
title: Cluster log in with SSH
date: 2019-05-05
type: book
summary: Don't enter your password every time you SSH into a cluster
---
## TL;DR
- Don't enter your password every time you SSH into a cluster

## Configure SSH
Add your cluster login details to your ssh config `~/.ssh/config` so that you can log in with
```sh
shh CLUSTER_NAME
```
Importantly, you should not need to enter your password.
Assuming you log into the cluster with 
```sh
ssh USERNAME@HOSTNAME
```
then your ssh config `~/.ssh/config` should have an entry like this
```sh
Host CLUSTER_NAME
  HostName HOSTNAME
  User USERNAME
  IdentityFile ~/.ssh/YOUR_PRIVATE_KEY
```
Then you can easily ssh into the cluster with
```sh
shh CLUSTER_NAME
```

