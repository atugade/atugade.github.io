---
layout: post
title:  "Starting minikube on macOS to learn kubernetes"
date:   2018-10-07
desc: "Starting minikube with options to do anything useful on kubernetes locally"
keywords: "kubernetes,docker,minikube,devops,gitops,blog"
categories: [HTML]
tags: [kubernetes,docker,minikube,devops,gitops]
icon: icon-html
---

I'm starting this blog just to document my own personal journey learning or prototyping things docker and kubernetes related.  I've been meaning to create documentation for the things I've been researching on my own for the past couple months like building docker images without docker, CI/CD, maintaining k8s cluster state, local development to name a few.  This post is just a quick little tidbit on how I launch minikube so I can actually do something useful on it locally on my laptop.

* OS: macOS 10.14 Mojave (18A391)
* Spec: MacBook Pro (Mid 2015)

I installed minikube via [Homebrew](https://brew.sh/).

Start minikube with a little more cpu and memory than the default settings:

```
$ minikube start --cpus 4 --memory 4096
```

If all goes well you should output similar to the following:

```
Starting local Kubernetes v1.10.0 cluster...
Starting VM...
Downloading Minikube ISO
 170.78 MB / 170.78 MB [============================================] 100.00% 0s
Getting VM IP address...
Moving files into cluster...
Downloading kubeadm v1.10.0
Downloading kubelet v1.10.0
Finished Downloading kubelet v1.10.0
Finished Downloading kubeadm v1.10.0
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.
$ 
```

Verify the k8s dashboard comes up in your browser:

```
$ minikube dashboard
```

If you plan on using the same shell you opened the dashboard in, you may want to background the previous command.  I like to see usage metrics of the workloads on the system so I always enable the heapster addon:

```
$ minikube addons enable heapster
heapster was successfully enabled
```

It takes some time for the graphs to come up in the dashboard interface, so lets start off with launching nginx into our cluster:

```
kubectl create deployment nginx1 --image=nginx
```

I found this a little special, that you can specify the name of the deployment as the name of the service and it's automagically associated:

```
kubectl create service nodeport nginx1 --tcp=80:80
```

Since the service was specified as type nodeport, you can use the service subcommand of minikube to bring up the site:

```
minikube service nginx1
```

Assuming several minutes have gone by since you brought up your nginx service, the dashboard should have some graphs on as shown below:

<center><img src="{{ site.img_path }}/article_000000/minikube-dashboard-heapster.png" width="75%"></center>

I do cleanup just so there are enough resources when I decide to run more intensive workloads.

```
$ kubectl delete service nginx1
service "nginx1" deleted
$ kubectl delete deployment nginx1
deployment.extensions "nginx1" deleted
```

This is enough for me personally to get up and running so I can start testing out some ideas and concepts in kubernetes.
