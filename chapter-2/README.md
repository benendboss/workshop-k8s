# Chapter 2

Installing an Ingress Controller with ingress-nginx

## Creating Namespace for Ingress Controller

`kubectl create ns ingress-nginx`

## Install Ingress Nginx via Helm

1. Add Repo zu helm

`helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx`

2. Update helm repositorys

`helm repo update`

3. Install the helm chart

`helm install ingress-nginx -n ingress-nginx ingress-nginx/ingress-nginx

4. Check the installation

`kubectl get all -n ingress-nginx`