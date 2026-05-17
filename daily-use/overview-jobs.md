---
description: Acompanhe importações, deleções, retries, cancelamentos e detalhes de jobs do Overview.
icon: list-checks
---

# Jobs ⚙️

Jobs mostra o trabalho em segundo plano criado por importações e deleções do Overview.

![Jobs do Overview](../.gitbook/assets/screenshots/overview.png)

## Por que jobs existem 🧠

Importações históricas podem levar tempo, especialmente com múltiplas instâncias Pi-hole. O YAPD mantém esse trabalho em segundo plano para que o Overview continue utilizável enquanto o job roda.

## Status de jobs 🚦

| Status | Significado |
| --- | --- |
| **Na fila** | Esperando para iniciar. |
| **Em execução** | Importação ou deleção em andamento. |
| **Pausado** | Execução pausada depois de falhas repetidas. |
| **Cancelado** | Cancelado antes de iniciar. |
| **Sucesso** | Concluiu com resultados utilizáveis. |
| **Parcial** | Concluiu, mas uma ou mais instâncias tiveram lacunas ou falhas. |
| **Falha** | Terminou sem resultados utilizáveis. |

## Ações 🛠️

Dependendo do status, você pode:

* abrir o período importado no Ranking;
* ver detalhes;
* tentar novamente jobs com falha, pausados, parciais ou cancelados;
* cancelar jobs enfileirados;
* apagar registros antigos de job e histórico do Overview vinculado.

{% hint style="warning" %}
⚠️ Apagar um job bem-sucedido, parcial, pausado, com falha ou cancelado pode remover dados históricos vinculados a esse job.
{% endhint %}

## Detalhes do job 🔎

O modal de detalhes inclui:

* resumo;
* escopo;
* origem, como importação manual ou automática;
* período;
* totais esperados e salvos;
* tentativas;
* percentual de progresso;
* motivo principal de falha;
* progresso por instância;
* linha do tempo de eventos.

Use esse modal quando uma importação falhar ou concluir apenas parcialmente.

## Motivos comuns de falha 🧯

| Motivo | O que conferir |
| --- | --- |
| **Timeout** | Disponibilidade da instância, latência ou comportamento do proxy. |
| **Session error** | Reautentique a instância. |
| **Server unavailable** | Confira se o Pi-hole está online. |
| **Count mismatch** | Tente novamente e compare o período afetado. |
| **Unexpected failure** | Revise os detalhes e os logs do YAPD. |
