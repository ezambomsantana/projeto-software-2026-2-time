# API de Cadastro de Times de Futebol

API simples desenvolvida com Flask e MongoDB para gerenciar times de futebol.

## Requisitos

- Docker e Docker Compose (recomendado)
- Ou Python 3.11+ e MongoDB instalados

## Configuração

### Com Docker Compose (Recomendado)

1. Clone o repositório e entre na pasta:

```bash
cd seu-projeto
```

2. Configure as variáveis de ambiente (opcional):

```bash
cp .env.example .env
```

3. Inicie os containers:

```bash
docker-compose up --build
```

A API estará disponível em `http://localhost:5000`

### Sem Docker

1. Certifique-se de que MongoDB está rodando em sua máquina

2. Crie um arquivo `.env` na raiz do projeto:

```
DB_HOST=localhost
DB_NAME=football_db
DB_PORT=27017
```

3. Instale as dependências:

```bash
pip install -r requirements.txt
```

4. Inicie a aplicação:

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

### Atualizar um time
```
PUT /times/<id>
Content-Type: application/json

{
  "nome": "Flamengo",
  "estadio": "Estádio Nilton Santos",
  "cidade": "Rio de Janeiro"
}
```

### Deletar um time
```
DELETE /times/<id>
```

### Verificar saúde da API
```
GET /health
```

## Exemplos de Uso

### Com curl

Criar um time:
```bash
curl -X POST http://localhost:5000/times \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "São Paulo FC",
    "estadio": "Morumbi",
    "cidade": "São Paulo"
  }'
```

Listar todos os times:
```bash
curl http://localhost:5000/times
```

Obter um time específico:
```bash
curl http://localhost:5000/times/1
```

Atualizar um time:
```bash
curl -X PUT http://localhost:5000/times/1 \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "São Paulo FC",
    "estadio": "Estádio do Morumbi",
    "cidade": "São Paulo"
  }'
```

Deletar um time:
```bash
curl -X DELETE http://localhost:5000/times/1
```

## Estrutura do Projeto

```
.
├── app.py                 # Aplicação principal Flask
├── requirements.txt       # Dependências Python
├── Dockerfile            # Configuração Docker
├── docker-compose.yml    # Orquestração de containers
├── .env.example         # Exemplo de variáveis de ambiente
└── README.md            # Este arquivo
```

## Variáveis de Ambiente

- `DB_HOST`: Host do MongoDB (padrão: localhost ou mongo no Docker)
- `DB_NAME`: Nome do banco de dados (padrão: football_db)
- `DB_PORT`: Porta do MongoDB (padrão: 27017)

## Parar e Remover Containers

```bash
docker-compose down
```

Para remover também o volume do MongoDB:

```bash
docker-compose down -v
```
