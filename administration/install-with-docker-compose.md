---
description: Escolha entre Compose completo, banco externo, arquivo copiado ou clone do repositório.
icon: download
---

# Instalar com Docker Compose 🐳

Docker Compose é a forma recomendada de rodar o YAPD para uso auto-hospedado normal.

Use uma das abas abaixo de acordo com o modelo de banco de dados e a forma como você prefere iniciar a instalação.

## O que será executado 📦

O Compose de produção pode rodar de duas formas:

* **Compose completo**: inicia o container **YAPD app** e um container **PostgreSQL** dedicado.
* **Banco externo**: inicia apenas o container **YAPD app** e conecta em um PostgreSQL externo já existente.

Em ambos os casos, o container do YAPD inclui interface web, API e Nginx interno.

As portas publicadas por padrão são:

| Porta | Uso |
| --- | --- |
| `48080` | Acesso HTTP ao YAPD |
| `48443` | Acesso HTTPS interno com certificado autoassinado |

{% hint style="info" %}
🌐 Se você usa proxy reverso externo, aponte-o para `http://<ip-do-servidor>:48080` e deixe o proxy cuidar do certificado HTTPS público.
{% endhint %}

## Métodos de instalação ⚡

{% tabs %}
{% tab title="Compose completo" %}
Use esta opção quando o YAPD também deve criar e gerenciar o container PostgreSQL.

Crie um arquivo `compose.yml` com este conteúdo:

```yaml
services:
  postgres:
    image: postgres:16-alpine
    restart: unless-stopped
    environment:
      - POSTGRES_DB=yapd
      - POSTGRES_USER=yapd
      - POSTGRES_PASSWORD=change-this-password
    volumes:
      - yapd-prod-postgres-data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -h localhost -U \"$${POSTGRES_USER}\" -d \"$${POSTGRES_DB}\""]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 10s

  yapd:
    image: leufrasiojunior/yapd:latest
    restart: unless-stopped
    depends_on:
      postgres:
        condition: service_healthy
    ports:
      - "48080:80"
      - "48443:443"
    environment:
      - NODE_ENV=production
      - PORT=3000
      - HOSTNAME=0.0.0.0
      - API_HOST=0.0.0.0
      - API_PORT=3001
      # Configure com a URL exata do navegador, por exemplo https://yapd.exemplo.com.
      - WEB_ORIGIN=https://example.domain.com
      - API_BASE_URL=/api
      - INTERNAL_API_BASE_URL=http://127.0.0.1:3001/api
      - NEXT_PUBLIC_API_BASE_URL=/api
      - YAPD_POSTGRES_HOST=postgres
      - YAPD_POSTGRES_DB=yapd
      - YAPD_POSTGRES_USER=yapd
      # Mantenha este valor igual ao POSTGRES_PASSWORD acima.
      - YAPD_POSTGRES_PASSWORD=change-this-password
      # Troque estes segredos antes de iniciar a stack.
      - SESSION_SECRET=change-this-session-secret
      - APP_ENCRYPTION_KEY=change-this-encryption-key
      # Notificações push exigem origem HTTPS confiável no navegador ou localhost.
      - WEB_PUSH_VAPID_SUBJECT=mailto:admin@yapd.local
      - COOKIE_SECURE=true
      - SWAGGER_ENABLED=false
      - YAPD_DB_MIGRATION_MAX_ATTEMPTS=30
      - YAPD_DB_MIGRATION_RETRY_DELAY_SECONDS=2
      - YAPD_API_READY_MAX_ATTEMPTS=30
      - YAPD_API_READY_RETRY_DELAY_SECONDS=1
    command:
      - bash
      - -c
      - |
        export DATABASE_URL="postgresql://$${YAPD_POSTGRES_USER}:$${YAPD_POSTGRES_PASSWORD}@$${YAPD_POSTGRES_HOST}:5432/$${YAPD_POSTGRES_DB}?schema=public"
        exec bash ./scripts/start-app-container.sh
    healthcheck:
      test:
        [
          "CMD-SHELL",
          "wget -qO- http://127.0.0.1:80/healthz >/dev/null 2>&1 && wget -qO- http://127.0.0.1:3001/api/health >/dev/null 2>&1 || exit 1"
        ]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 45s

volumes:
  yapd-prod-postgres-data:
```

Antes de iniciar, troque `POSTGRES_PASSWORD`, `YAPD_POSTGRES_PASSWORD`, `SESSION_SECRET`, `APP_ENCRYPTION_KEY` e `WEB_ORIGIN`. Os dois valores de senha do Postgres devem ser iguais.

```bash
docker compose up -d
```
{% endtab %}

{% tab title="BD externo" %}
Use esta opção quando você já tem um PostgreSQL externo e quer rodar apenas o container do YAPD.

Crie um arquivo `compose.yml` com este conteúdo:

```yaml
services:
  yapd:
    image: leufrasiojunior/yapd:latest
    restart: unless-stopped
    ports:
      - "48080:80"
      - "48443:443"
    environment:
      - NODE_ENV=production
      - PORT=3000
      - HOSTNAME=0.0.0.0
      - API_HOST=0.0.0.0
      - API_PORT=3001
      # Configure com a URL exata do navegador, por exemplo https://yapd.exemplo.com.
      - WEB_ORIGIN=https://example.domain.com
      - API_BASE_URL=/api
      - INTERNAL_API_BASE_URL=http://127.0.0.1:3001/api
      - NEXT_PUBLIC_API_BASE_URL=/api
      # Configure estes valores para o seu PostgreSQL externo.
      - YAPD_POSTGRES_HOST=postgres.example.internal
      - YAPD_POSTGRES_DB=yapd
      - YAPD_POSTGRES_USER=yapd
      - YAPD_POSTGRES_PASSWORD=change-this-password
      # Troque estes segredos antes de iniciar a stack.
      - SESSION_SECRET=change-this-session-secret
      - APP_ENCRYPTION_KEY=change-this-encryption-key
      # Notificações push exigem origem HTTPS confiável no navegador ou localhost.
      - WEB_PUSH_VAPID_SUBJECT=mailto:admin@yapd.local
      - COOKIE_SECURE=true
      - SWAGGER_ENABLED=false
      - YAPD_DB_MIGRATION_MAX_ATTEMPTS=30
      - YAPD_DB_MIGRATION_RETRY_DELAY_SECONDS=2
      - YAPD_API_READY_MAX_ATTEMPTS=30
      - YAPD_API_READY_RETRY_DELAY_SECONDS=1
    command:
      - bash
      - -c
      - |
        export DATABASE_URL="postgresql://$${YAPD_POSTGRES_USER}:$${YAPD_POSTGRES_PASSWORD}@$${YAPD_POSTGRES_HOST}:5432/$${YAPD_POSTGRES_DB}?schema=public"
        exec bash ./scripts/start-app-container.sh
    healthcheck:
      test:
        [
          "CMD-SHELL",
          "wget -qO- http://127.0.0.1:80/healthz >/dev/null 2>&1 && wget -qO- http://127.0.0.1:3001/api/health >/dev/null 2>&1 || exit 1"
        ]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 45s
```

O PostgreSQL externo precisa estar acessível a partir do container do YAPD na porta `5432`. Se o banco usa outra porta, ajuste a porta no `DATABASE_URL` montado no bloco `command`.

{% hint style="warning" %}
Crie o banco manualmente antes de iniciar o YAPD. O nome do banco deve ser igual a `YAPD_POSTGRES_DB`, e `YAPD_POSTGRES_USER` precisa ter permissão para criar e atualizar tabelas nesse banco.
{% endhint %}

```bash
docker compose up -d
```
{% endtab %}

{% tab title="Copiando o Compose" %}
Use esta opção quando você quer baixar o arquivo oficial do repositório e editar localmente.

{% stepper %}
{% step %}
### Baixe o arquivo Compose 📥

```bash
curl -O https://raw.githubusercontent.com/leufrasiojunior/yadp/main/compose.yml
```
{% endstep %}

{% step %}
### Edite os valores obrigatórios ✏️

Abra `compose.yml` e altere pelo menos:

* `POSTGRES_PASSWORD`
* `YAPD_POSTGRES_PASSWORD`
* `SESSION_SECRET`
* `APP_ENCRYPTION_KEY`
* `WEB_ORIGIN`

Os dois valores de senha do Postgres devem ser iguais.
{% endstep %}

{% step %}
### Inicie o YAPD ▶️

```bash
docker compose up -d
```
{% endstep %}

{% step %}
### Abra o app 🌐

Acesse:

```text
http://<ip-do-servidor>:48080
```

Depois conclua [Primeiro acesso e setup](../start-here/first-access-and-setup.md).
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="Clonando o repositório" %}
Use esta opção quando você quer manter o arquivo Compose junto com o repositório local.

{% stepper %}
{% step %}
### Clone o repositório 📦

```bash
git clone https://github.com/leufrasiojunior/yadp.git
cd yadp
```
{% endstep %}

{% step %}
### Edite o Compose ✏️

Abra `compose.yml` e altere `POSTGRES_PASSWORD`, `YAPD_POSTGRES_PASSWORD`, `SESSION_SECRET`, `APP_ENCRYPTION_KEY` e `WEB_ORIGIN`.
{% endstep %}

{% step %}
### Inicie o YAPD ▶️

```bash
docker compose -f compose.yml up -d
```
{% endstep %}

{% step %}
### Abra o app 🌐

Acesse `http://<ip-do-servidor>:48080` e conclua [Primeiro acesso e setup](../start-here/first-access-and-setup.md).
{% endstep %}
{% endstepper %}
{% endtab %}
{% endtabs %}

## Valores importantes 🔐

| Valor | O que configurar |
| --- | --- |
| `POSTGRES_PASSWORD` | Senha forte para o container Postgres no Compose completo. |
| `YAPD_POSTGRES_HOST` | Host do PostgreSQL usado pelo YAPD. No Compose completo, mantenha `postgres`. |
| `YAPD_POSTGRES_DB` | Nome do banco usado pelo YAPD. |
| `YAPD_POSTGRES_USER` | Usuário do banco usado pelo YAPD. |
| `YAPD_POSTGRES_PASSWORD` | Senha do banco usada pelo YAPD. No Compose completo, deve ser igual a `POSTGRES_PASSWORD`. |
| `SESSION_SECRET` | Segredo longo e aleatório para sessões do YAPD. |
| `APP_ENCRYPTION_KEY` | Segredo longo e aleatório usado para dados criptografados da aplicação. |
| `WEB_ORIGIN` | URL exata usada no navegador, como `https://yapd.exemplo.com`. |
| `COOKIE_SECURE` | Use `true` quando o navegador acessar o YAPD por HTTPS. Use `false` somente para acesso HTTP simples. |
| `WEB_PUSH_VAPID_SUBJECT` | Contato usado pelo serviço de notificações push, normalmente no formato `mailto:admin@seudominio.com`. |

{% hint style="danger" %}
🚫 Não reutilize os segredos de exemplo do arquivo Compose em uma instalação real.
{% endhint %}

## Comandos básicos 🧰

| Tarefa | Comando |
| --- | --- |
| Iniciar | `docker compose up -d` |
| Parar | `docker compose down` |
| Ver logs do app | `docker compose logs --tail=200 yapd` |
| Ver logs do banco no Compose completo | `docker compose logs --tail=200 postgres` |
| Ver containers | `docker compose ps` |

## Depois da instalação ✅

Continue em:

* [Primeiro acesso e setup](../start-here/first-access-and-setup.md)
* [Proxy reverso e HTTPS](reverse-proxy-and-https.md)
* [Operação segura](safe-operation.md)
