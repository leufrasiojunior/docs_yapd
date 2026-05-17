---
description: Importe dias fechados e entenda a cobertura disponível no Overview.
icon: calendar-days
---

# Período e cobertura 📅

Período e cobertura é onde você escolhe um dia fechado, solicita importação histórica, apaga histórico salvo e vê quais dados do Overview estão disponíveis.

![Período e cobertura do Overview](../.gitbook/assets/screenshots/overview.png)

## Escolha um dia 🎯

Use **Date**, **From** e **Until** para escolher o período.

Para importações manuais:

* o período deve ficar dentro de um único dia civil;
* o dia precisa estar fechado;
* a data atual não pode ser importada;
* os horários ainda podem ser ajustados dentro do dia selecionado.

## Solicitar importação 📥

Clique em **Solicitar importação** para enfileirar um job em segundo plano.

Depois de enfileirar:

1. O YAPD cria um job.
2. A tela continua utilizável.
3. O progresso aparece em **Overview > Jobs**.
4. Notificações são criadas quando a importação conclui, conclui parcialmente ou falha.

## Apagar período 🗑️

Use **Apagar período** quando quiser remover o histórico salvo do Overview para o período selecionado.

{% hint style="warning" %}
⚠️ Apagar um período do Overview remove linhas históricas armazenadas localmente. Isso não apaga dados do Pi-hole, mas o Ranking não terá esse período até você importá-lo novamente.
{% endhint %}

## Cobertura disponível 🧾

Cobertura mostra o que o YAPD já tem salvo:

* quantidade de queries armazenadas;
* registro mais antigo e mais recente;
* períodos salvos concluídos ou parciais;
* períodos próximos de expirar;
* cobertura que pode ser renovada.

## Renovar cobertura 🔄

Quando um período salvo está perto de expirar, o YAPD pode renová-lo por mais 30 dias sem buscar os dados novamente.

Use **Renovar +30 dias** quando você ainda precisa daquele período histórico disponível para análises futuras no Ranking.
