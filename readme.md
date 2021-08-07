# Otus microservice architecture HW6
## Helm

For running HW please execute the next commands
```bash
//if you use Minikube execute the following commands
minikube start
minikube addons enable metallb
minikube addins enable ingress

//install postgres from bitnami repo with helm
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install pg helm_postgres/bitnami_postgresql.yaml 

//install hw service from charts in this repo
helm install helm_app 
```

For checking HW please execute the following cURLSs
```bash
// post new user
curl --location --request POST 'http://arch.homework/user' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 1,
    "username": "username1",
    "firstName": "firstName1",
    "lastName": "lastName1",
    "email": "email1",
    "phone": "phone1"
}'
// get saved user
curl --location --request GET 'http://arch.homework/user/1' \
--header 'Accept: application/json'
```