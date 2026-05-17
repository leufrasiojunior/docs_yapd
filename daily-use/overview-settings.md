---
description: Agende importações recorrentes do Overview para dias fechados.
icon: settings
---

# Configurações do Overview ⏰

Configurações do Overview permite criar regras de importação automática que enfileiram jobs de coleta histórica.

![Configurações do Overview](../.gitbook/assets/screenshots/overview.png)

## O que a importação automática faz 🤖

Uma regra automática agenda a coleta do Overview. A regra decide quando rodar, mas a janela importada continua sendo o dia anterior completo no fuso horário configurado na aplicação.

Exemplo: uma regra diária às `03:00` importa o dia `d-1` completo.

## Campos da regra 📝

| Campo | Significado |
| --- | --- |
| **Nome** | Nome amigável da regra. |
| **Ativa** | Regras desativadas continuam salvas, mas não agendam jobs. |
| **Instância** | Escolha todas as instâncias ou uma instância específica. |
| **Preset** | Use presets diários ou horários, ou informe uma expressão cron customizada. |
| **Cron** | Expressão final de agendamento usada pela regra. |

## Presets de agendamento ⚡

Os presets disponíveis incluem:

* todos os dias às `03:00`;
* todos os dias às `00:00`;
* todos os dias às `06:00`;
* a cada hora;
* expressão customizada.

{% hint style="info" %}
📌 Importações automáticas aparecem em [Jobs](overview-jobs.md), assim como importações manuais.
{% endhint %}

## Quando usar ✅

Use importações automáticas quando quiser que rankings do Overview estejam prontos todos os dias sem precisar importar o dia anterior manualmente.
