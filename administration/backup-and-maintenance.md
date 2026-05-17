---
description: Mantenha o YAPD e seus dados recuperáveis durante a operação normal.
icon: database-backup
---

# Backup e manutenção 💾

O YAPD salva seus próprios dados no PostgreSQL, incluindo estado de setup, instâncias cadastradas, notificações, preferências e histórico local importado pelo Overview.

## O que fazer backup 🧳

Faça backup de:

* volume PostgreSQL usado pelo YAPD;
* seu `compose.yml` editado;
* configuração do proxy reverso externo;
* notas sobre URLs dos Pi-holes, escolhas de certificado e modo de login.

{% hint style="info" %}
📌 O YAPD não substitui backups do Pi-hole. Continue fazendo backup das instâncias Pi-hole separadamente.
{% endhint %}

## Antes de mudanças de risco ✅

Crie backup antes de:

* alterar o Compose de produção;
* mover o YAPD para outro servidor;
* trocar segredos;
* executar sync de configuração em lote;
* apagar grandes períodos históricos do Overview.

## Checagens de manutenção 🧰

Use estas checagens durante a operação normal:

```bash
docker compose ps
docker compose logs --tail=200 yapd
docker compose logs --tail=200 postgres
```

Depois confira a interface:

* **Instâncias**: procure sessões expiradas ou falhas de validação.
* **Notificações**: marque eventos esperados como lidos e revise falhas.
* **Overview > Jobs**: confira jobs com falha, pausados ou parciais.
* **Configurações**: revise drift antes de sincronizar.

## Atualizando o YAPD ⬆️

Uma atualização normal costuma significar baixar a imagem nova e reiniciar:

```bash
docker compose pull
docker compose up -d
```

Depois da atualização, abra o YAPD e confirme:

* login funcionando;
* baseline ainda correta;
* instâncias cadastradas testando com sucesso;
* Overview jobs e Notificações carregando.
