# Kubernetes Bootcamp 2.0
Criação do Dockerfile e .dockerignore. Aplicação do NodeJS **não** foi desenvolvida por mim.

## Passos relacionados ao Docker:

No diretório da aplicação, use o seguinte comando para construir a imagem:
```
docker build -t leandromusser/api-conversao:v1 .
```
A imagem também pode ser obtida pelo repositório no Docker Hub (https://hub.docker.com/r/leandromusser/api-conversao). Nesse caso, usar o seguinte comando ao invés do de cima:
```
docker pull leandromusser/api-conversao:v1
```
Depois, caso **não** opte por usar o Kubernetes, instancie o container com:
```
docker run -dp 8080:8080 leandromusser/api-conversao:v1
```
O primeiro 8080 pode ser alterado para outra porta, é por onde acessaremos a aplicação. 
Acesse **localhost:8080** para ver o funcionamento.

## Passos relacionados ao Kubernetes:

Estou utilizando o k3d para desenvolvimento local. Tendo ele e o kubectl instalados, use o seguinte comando:

```
k3d cluster create --agents 3 --servers 3 -p "8080:30000@loadbalancer"
```
8080 é a porta por onde acessaremos teremos acesso à aplicação. Escolha os melhores valores para você.
Em seguida, no diretório Kubernetes, onde estão os arquivos service.yaml e deployment.yaml, use o seguinte comando:
```
kubectl apply -f Kubernetes
```
Onde Kubernetes é o diretório onde estão aqueles arquivos. Isso irá criar o deployment e service. 
Acesse **localhost:8080** para ver o funcionamento (pode levar algum tempo). Use o seguinte comando para verificar o status dos pods:
```
kubectl get pods
```