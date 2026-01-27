# m7011e-gitops

# Kubernetess
Kubernetes is used to orchestrate, deploy, and manage containerized microservices.

# argo-cd
Handles the application and syncronizes to this repository. To make a new application. To make a new application, either with UI or just run

```
kubectl apply -f application-argo.yaml
```
Useful commands
```
kubectl get pods -n namespace
kubectl get svc -n namespace
```

TO update argocd for frontend and backend, change redeployAt

# keycloak
Will mainly be used to handle user login and register. It will hash the password for us and when logging in it sends back an jwt token which shows ownership.

There is also possible to make different roles depending on what you log in as.

Where to login as admin:
https://keycloak-dev.ltu-m7011e-7.se/admin

# Postgres database
Make sure that the service name is correct
```
kubectl get svc -n database-dev
```

Then
```
kubectl port-forward -n database-dev svc/postgres-service 55432:5432
```

After this we can with the values.yaml for postgres see the database in pgadmin UI

# Rabbitmq
Rabbitmq works as a message broker for asynchronous communication between services. This will make sure that data isn't lost if the system crashes or something unexpected happens.

# Grafana and prometheus
Prometheus exposes a metrics endpoint. It scrapes those enpoints and it is stored as a time-series data. 

Grafana is a visualization tool which connects to prometheus. It can visualize the data as graphs and can also define alerts. 

Port forward to grafana
```
kubectl port-forward -n monitoring svc/grafana 3000:3000
```

Go to Home -> Dashboards -> RabbitMQ Monitoring Dashboard

If we in the future wants do deploy stages we could 

dev looking at dev branch
Stage looking at stage branch
production looking at main


To run kubernetess deployment
```
https://frontend-dev.ltu-m7011e-7.se
```
