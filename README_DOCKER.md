# Instruções básicas para Docker (projeto multi-app)

Pré-requisitos:
- Docker e Docker Compose instalados.

Build e subir todos os serviços:

```powershell
docker-compose build
docker-compose up -d
```

Ver logs de um serviço (ex.: `aluno_app`):

```powershell
docker-compose logs -f aluno_app
```

Build e rodar um serviço isolado (opcional):

```powershell
docker build -t aluno_app ./aluno_app
docker run -p 3001:3000 --env NODE_ENV=production aluno_app
```

Notas:
- Cada `Dockerfile` assume que o ponto de entrada é `server.js` na raiz da pasta da aplicação. Se algum serviço usar outro arquivo de entrada, ajuste o `CMD` no `Dockerfile` correspondente.
- As portas mapeadas no `docker-compose.yml` são `3001..3006` e encaminham para `3000` dentro do container — ajuste conforme necessário.
- Remova ou ajuste `--only=production` na instalação se você precisar de dependências de desenvolvimento no container.
