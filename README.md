# Projeto pedelogo-catalogo

### Sobre o projeto
O projeto pedelogo-catalogo é um projeto desenvolvido em .NET. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando .NET.

### Criação do cluster
k3d cluster create meucluster --agents 3 --servers 2 -p 80:30000@loadbalancer" -p "8080:31000@loadbalancer" -p "8282:32000@loadbalancer" -p "9090:31500@loadbalancer"

### Observação do inicio do cluster
Executar kubectl apply -f k8s/db -f k8s/api

### Criação do namespace
kubectl create ns loki

### Criação do Loki
helm upgrade --install loki grafana/loki-stack --namespace loki --values values-loki.yaml

### Comando para pegar o password do grafana
kubectl get secret --namespace loki loki-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

### Acesso das ferramentas
Prometheus: http://localhost:8080/
Alert Manager: http://localhost:8282/
Application: http://localhost/swagger
Grafana: http://localhost:9090/
Promtail: Para acesso do promtail, terá que ser feito um port-forward de um dos pods, kubectl port-forward pod/NOME_POD 3101:3101 e então acessar http://localhost:3101




# Project pedelogo-catalogo

### About the project
The project pedelogo-catalogo is a project developed in .NET. The project goal is to be a example to environment creation with containers using .NET.

### Cluster creation
k3d cluster create meucluster --agents 3 --servers 2 -p 80:30000@loadbalancer" -p "8080:31000@loadbalancer" -p "8282:32000@loadbalancer" -p "9090:31500@loadbalancer"

### Cluster initialization
Executar kubectl apply -f k8s/db -f k8s/api

### Creation of namespace
kubectl create ns loki

### Creation of Loki
helm upgrade --install loki grafana/loki-stack --namespace loki --values values-loki.yaml

### Command for get the password for grafana
kubectl get secret --namespace loki loki-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

### Access features:
Prometheus: http://localhost:8080/
Alert Manager: http://localhost:8282/
Aplicação: http://localhost/swagger
Grafana: http://localhost:9090/
Promtail: For access promtail, you have to use port-forward of one of the pods, kubectl port-forward pod/POD_NAME 3101:3101 then access http://localhost:3101