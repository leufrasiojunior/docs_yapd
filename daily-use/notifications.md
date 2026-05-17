---
description: Revise eventos armazenados, falhas e estado de notificações push no navegador.
icon: bell
---

# Notificações 🔔

Notificações centraliza eventos do YAPD, mensagens do Pi-hole e falhas operacionais recentes.

![Notificações do YAPD](../.gitbook/assets/screenshots/notifications.png)

## O que aparece aqui 📬

Notificações podem incluir:

* erros de conexão;
* falhas de sessão;
* falhas de sync;
* resultados de importação do Overview;
* resultados de deleção do Overview;
* renovações de cobertura do Overview;
* falhas de coletores;
* falhas do sistema.

## Abas não lidas e lidas 🗂️

Use as abas para separar eventos não lidos de eventos antigos já lidos. Você pode marcar uma notificação como lida ou marcar todas as notificações visíveis como lidas.

## Títulos de falha mais claros 🧯

O YAPD tenta mostrar títulos legíveis em vez de códigos técnicos crus.

Títulos comuns incluem:

* credenciais inválidas;
* erro de TLS;
* timeout de conexão;
* erro de DNS;
* conexão recusada;
* erro de resposta do Pi-hole.

## Notificações push 📲

Notificações push podem ser ativadas por navegador/dispositivo quando o deploy suporta esse recurso.

Push exige:

* HTTPS com certificado confiável, ou localhost;
* suporte do navegador a push notifications;
* permissão do navegador definida como permitida;
* configuração de push disponível no servidor.

{% hint style="warning" %}
🔒 Push normalmente não funciona pelo acesso direto `http://<ip-do-servidor>:48080`. Use um domínio HTTPS confiável por proxy reverso.
{% endhint %}
