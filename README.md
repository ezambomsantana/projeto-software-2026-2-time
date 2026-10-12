# API de Cadastro de Times de Futebol


## Como Executar

1. Crie a rede Docker (se não foi criada ainda)

```
docker network create -d bridge rede
```

2. Certifique-se de que MongoDB está rodando em sua máquina

```
docker run -p 27017:27017 --network=rede --name mongo mongo
```

2. Instale as dependências:

```bash
pip install -r requirements.txt
```

3. Mude os parâmetros do GitHub Action

no arquivo /.github/workflows/deploy.yml existem 3 valores,
mude os nomes de usuário para o seu usuário do DockerHub

```
env:
  DOCKER_IMAGE: ezambomsantana/time-ci
  CONTAINER_NAME: time
  DOCKER_USER: ezambomsantana
```


## Endpoints

### Listar todos os times
```
GET /times
```

### Obter um time específico
```
GET /times/<id>
```

### Criar um novo time
```
POST /times
Content-Type: application/json

{
  "nome": "sFlamengo",
  "estadio": "Maracanã",
  "cidade": "Rio de Janeiro"
}
```

### Verificar saúde da API
```
GET /health
```