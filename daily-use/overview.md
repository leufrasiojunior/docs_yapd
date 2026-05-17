---
description: Entenda a tela Overview do YAPD e como ela difere do Dashboard e do Queries Log.
icon: activity
---

# Overview 📊

Overview é a tela de análise histórica do YAPD. Ela lê histórico de queries salvo no banco local do YAPD e transforma esse histórico em cobertura, rankings, gráficos e visibilidade de jobs em segundo plano.

![Overview do YAPD](../.gitbook/assets/screenshots/overview.png)

Abra pela sidebar em **Overview** ou acesse diretamente `/overview`.

## Por que o Overview é diferente 🧠

Dashboard e Queries Log ficam mais próximos da atividade ao vivo do Pi-hole. O Overview é diferente porque trabalha com dados históricos importados.

Isso significa que:

* você solicita importações de dias fechados;
* o YAPD salva as linhas históricas localmente;
* rankings e gráficos usam apenas os dados salvos;
* jobs em segundo plano continuam rodando sem bloquear a tela;
* você pode inspecionar progresso, falhas, retries e deleções.

{% hint style="info" %}
📌 Se o Overview estiver vazio depois de uma instalação nova, normalmente ainda não há nenhum dia histórico importado.
{% endhint %}

## Abas do Overview 🧭

O Overview tem quatro abas:

| Aba | Use para |
| --- | --- |
| **Período e cobertura** | Solicitar importação manual, apagar um período salvo e revisar qual histórico está disponível. |
| **Ranking** | Analisar domínios, clientes, upstreams, status, distribuição por hora e períodos filtrados. |
| **Jobs** | Acompanhar importações e deleções em segundo plano, incluindo progresso e falhas. |
| **Configurações** | Criar regras de importação automática para coleta histórica recorrente. |

A aba selecionada também pode aparecer na URL, por exemplo `/overview?tab=ranking` ou `/overview?tab=jobs`.

## Importações manuais 📅

A coleta manual do Overview aceita um dia fechado por vez. O período padrão é o dia anterior fechado, de `00:00` até `23:59`, no fuso horário da aplicação.

O dia atual é bloqueado porque ainda está mudando.

## Links úteis 🔗

* [Período e cobertura](overview-period-and-coverage.md)
* [Ranking](overview-ranking.md)
* [Jobs](overview-jobs.md)
* [Configurações do Overview](overview-settings.md)
