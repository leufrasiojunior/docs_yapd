---
description: Use o Dashboard para acompanhar uma visão consolidada e ao vivo das suas instâncias Pi-hole.
icon: gauge
---

# Dashboard 📈

Dashboard é a tela diária para conferir a atividade atual do Pi-hole em uma ou mais instâncias cadastradas.

![Dashboard do YAPD](../.gitbook/assets/screenshots/dashboard.png)

## O que você vê 👀

O Dashboard mostra:

* total de queries;
* queries bloqueadas;
* percentual de bloqueio;
* total de domínios em ad-lists;
* volume de queries nas últimas 24 horas;
* clientes com mais atividade nas últimas 24 horas;
* avisos quando apenas parte das instâncias respondeu.

## Escolha o escopo 🎯

Use o seletor **Escopo** para alternar entre:

* **Todas as instâncias**: combina dados de todas as instâncias operacionais disponíveis.
* **Uma instância**: mostra apenas um Pi-hole.

{% hint style="info" %}
📌 Dashboard é uma tela operacional ao vivo. Para análise histórica, use [Overview](overview.md).
{% endhint %}

## Dados parciais ⚠️

Se uma ou mais instâncias não responderem, o YAPD mantém os dados saudáveis visíveis e mostra um aviso de dados parciais.

Quando isso acontecer:

1. Abra **Instâncias**.
2. Teste a instância com falha.
3. Reautentique se a sessão expirou.
4. Confira **Notificações** para ver um motivo de falha mais claro.

## Quando usar o Dashboard ✅

Use o Dashboard quando quiser entender o que está acontecendo agora:

* depois de alterar uma regra de bloqueio;
* depois de adicionar ou remover uma ad-list;
* quando um cliente parecer ativo demais;
* quando quiser uma checagem rápida antes de fazer sync.
