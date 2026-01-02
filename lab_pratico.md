
# Laboratório (Mão na Massa)

**Público-alvo:** Devs / DevOps iniciantes a intermediários  
**Pré-requisitos:** Terminal, Git, editor (VS Code), noções de HTTP  

---

## Objetivos

Ao final deste laboratório, você será capaz de:

- Entender imagens, containers, volumes e redes
- Executar e inspecionar containers
- Criar imagens com Dockerfile
- Utilizar Docker Compose
- Aplicar boas práticas básicas de segurança

---

## 1. Preparação do Ambiente

### 1.1 Verificação
```bash
docker version
docker info
docker compose version
```

### 1.2 Primeiro Container
```bash
docker run --rm hello-world
```

### 1.3 Imagens

Visualizando imagens disponíveis localmente

```bash
docker images
```

---

## 2. Conceitos Essenciais

- Imagem
- Container
- Volume
- Network
- Registry

---

## 3. Laboratório 1 — Comandos Básicos

```bash
docker run -d --name web -p 8080:80 nginx:alpine
docker ps
docker logs web
docker exec -it web sh
```

## 3.1 Opções do docker

Opções:
* -i: mantem o STDIN aberto, mesmo que não conecte ao container
* -t: disponibiliza um TTY (console) do container
* -d: modo daemon ou seja, sem interatividade, roda em background como um serviço


---


## 4. Laboratório 2 — Volumes

```bash
docker volume create dados
docker run -d --name db -v dados:/var/lib/postgresql/data postgres:16-alpine
```

---

## 5. Laboratório 3 — Redes

```bash
docker network create labnet
```

---

## 6. Laboratório 4 — Dockerfile

```Dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "main.py"]
```

---

## 7. Laboratório 5 — Docker Compose

```yaml
services:
  app:
    build: .
    ports:
      - "8000:8000"
```

---

## 8. Boas Práticas

- Usar imagens pequenas
- Evitar root
- Não commitar segredos

---

## 9. Desafios

1. Criar API + DB com Compose
2. Criar Dockerfile seguro
3. Subir múltiplas instâncias

---

## 10. Referência Rápida

```bash
docker ps
docker build -t img .
docker compose up -d
```
