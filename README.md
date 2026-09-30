# API de Cadastro de Times de Futebol

API simples desenvolvida com Flask e MongoDB para gerenciar times de futebol.

## Requisitos

- Docker e Docker Compose (recomendado)
- Ou Python 3.11+ e MongoDB instalados

## Como Executar

1. Certifique-se de que MongoDB está rodando em sua máquina

```
docker run -p 27017:27017 --name mongo mongo
```

2. Instale as dependências:

```bash
pip install -r requirements.txt
```

3. Inicie a aplicação:

```bash
python app.py
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
  "nome": "Flamengo",
  "estadio": "Maracanã",
  "cidade": "Rio de Janeiro"
}
```

### Verificar saúde da API
```
GET /health
```