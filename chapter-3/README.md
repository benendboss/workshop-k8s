# Chapter 3

## Installing a apache webserver

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: apache
  labels:
    app: apache
spec:
  replicas: 3
  selector:
    matchLabels:
      app: apache
  template:
    metadata:
      labels:
        app: apache
    spec:
      containers:
      - name: apache
        image: httpd:2.4
        ports:
        - containerPort: 80
´´´

## Create Service for apache

```
apiVersion: v1
kind: Service
metadata:
  name: apache
spec:
  selector:
    app: apache
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

## Create ingress resource to make service accessable from internet via ingress nginx

```
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  annotations:
    kubernetes.io/ingress.class: nginx
  name: apache 
spec:
  rules:
  - host: apache.teamk8s.de
    http:
      paths:
      - backend:
          serviceName: apache
          servicePort: 80
        path: /
```