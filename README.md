# Kubernetes Bootcamp 2.0
Criação do Dockerfile e .dockerignore. Aplicação do NodeJS **não** foi desenvolvida por mim.

## Passos relacionados ao Docker:

No diretório da aplicação, use o comando:
```
docker build -t leandromusser/api-conversao:v1 .
```
Depois instancie o container com:
```
docker run -dp 8080:8080 leandromusser/api-conversao:v1
```
O primeiro 8080 pode ser alterado para outra porta, é por onde acessaremos a aplicação. 
Acesse **localhost:8080** para ver o funcionamento.
