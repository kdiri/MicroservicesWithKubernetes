# App

A sample 12 Factor Application.

## Usage

Generate TLS certificates:

```
$ go run certgen/main.go
```
```
wrote ca.pem
wrote ca-key.pem
wrote server.pem
wrote server-key.pem
```

### Build and Run

```
$ go build -o server ./monolith
```

```
$ ./server
```

```
2016/04/15 06:34:12 Starting server...
2016/04/15 06:34:12 HTTP service listening on 0.0.0.0:80
2016/04/15 06:34:12 Health service listening on 0.0.0.0:81
2016/04/15 06:34:12 Started successfully.
```

### Test with cURL

```
$ curl --cacert ./ca.pem -u user https://127.0.0.1:80/login
```
```
Enter host password for user 'user':
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InVzZXJAZXhhbXBsZS5jb20iLCJleHAiOjE0NjA5ODcxOTcsImlhdCI6MTQ2MDcyNzk5NywiaXNzIjoiYXV0aC5zZXJ2aWNlIiwic3ViIjoidXNlciJ9.x3oFhRhWk5CGYfGcrNctPGWCENEsXpUuKPDQU2ZOLCY
```

> type "password" at the prompt

```
curl --cacert ./ca.pem -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InVzZXJAZXhhbXBsZS5jb20iLCJleHAiOjE0NjA5ODcxOTcsImlhdCI6MTQ2MDcyNzk5NywiaXNzIjoiYXV0aC5zZXJ2aWNlIiwic3ViIjoidXNlciJ9.x3oFhRhWk5CGYfGcrNctPGWCENEsXpUuKPDQU2ZOLCY' https://127.0.0.1:5000/
```
```
<h1>Hello</h1>
```

### Some Useful K8s Commands
```
kubectl run nginx --image=nginx:1.10.0
kubectl get nodes
kubectl get pods
kubectl describe pods monolith
kubectl create deployment nginx --image=nginx:1.10.0
kubectl create deployment nginx --port 80 --type LoadBalancer
kubectl get service
kubectl config view
# Enter into container
kubectl exec monolith --stdin --tty -c monolith /bin/sh
```
https://kubernetes.io/docs/reference/kubectl/cheatsheet/
