---
description: Instale o YAPD com o arquivo Docker Compose de produção.
icon: download
---

# Instalar com Docker Compose 🐳

Docker Compose é a forma recomendada de rodar o YAPD para uso auto-hospedado normal.

## O que será executado 📦

O Compose de produção inicia:

* um container **YAPD app** com interface web, API e Nginx interno;
* um container **PostgreSQL** para os dados do YAPD;
* uma rede privada Docker;
* um volume persistente para o Postgres.

As portas publicadas por padrão são:

| Porta | Uso |
| --- | --- |
| `48080` | Acesso HTTP ao YAPD |
| `48443` | Acesso HTTPS interno com certificado autoassinado |

{% hint style="info" %}
🌐 Se você usa proxy reverso externo, aponte-o para `http://<ip-do-servidor>:48080` e deixe o proxy cuidar do certificado HTTPS público.
{% endhint %}

## Instalação rápida ⚡

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

* `postgres_password`
* `session_secret`
* `app_encryption_key`
* `web_origin`

Use valores únicos para sua instalação.
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

## Valores importantes 🔐

| Valor | O que configurar |
| --- | --- |
| `postgres_password` | Uma senha forte para o Postgres. |
| `session_secret` | Um segredo longo e aleatório para sessões do YAPD. |
| `app_encryption_key` | Um segredo longo e aleatório usado para dados criptografados da aplicação. |
| `web_origin` | A URL exata usada no navegador, como `https://yapd.exemplo.com`. |
| `cookie_secure` | Use `true` quando o navegador acessar o YAPD por HTTPS. Use `false` somente para acesso HTTP simples. |

{% hint style="danger" %}
🚫 Não reutilize os segredos de exemplo do arquivo Compose em uma instalação real.
{% endhint %}

## Comandos básicos 🧰

| Tarefa | Comando |
| --- | --- |
| Iniciar | `docker compose up -d` |
| Parar | `docker compose down` |
| Ver logs do app | `docker compose logs --tail=200 yapd` |
| Ver logs do banco | `docker compose logs --tail=200 postgres` |
| Ver containers | `docker compose ps` |

## Depois da instalação ✅

Continue em:

* [Primeiro acesso e setup](../start-here/first-access-and-setup.md)
* [Proxy reverso e HTTPS](reverse-proxy-and-https.md)
* [Operação segura](safe-operation.md)
