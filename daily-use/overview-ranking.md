---
description: Use o Ranking do Overview para analisar domínios, clientes, upstreams e status históricos.
icon: bar-chart-3
---

# Ranking 🏆

Ranking transforma o histórico importado pelo Overview em gráficos, tabelas e filtros clicáveis.

![Ranking do Overview](../.gitbook/assets/screenshots/overview.png)

## Escolha datas salvas 📆

Os controles de **Datas salvas** definem o período usado pelo Ranking. Dias com registros armazenados são destacados, para que você selecione apenas períodos que realmente existem no YAPD.

Se não houver datas salvas, importe um dia fechado em [Período e cobertura](overview-period-and-coverage.md).

## Aplique filtros 🔍

Você pode filtrar por:

* período;
* domínio;
* IP do cliente;
* agrupamento por hora ou dia.

Clique em **Aplicar** para recarregar gráficos e tabelas. Clique em **Limpar** para voltar ao período mais amplo.

## O que o Ranking mostra 📊

O Ranking pode mostrar:

* total de queries;
* queries permitidas;
* queries bloqueadas;
* percentual de bloqueio;
* principais domínios;
* principais clientes;
* principais upstreams;
* principais status;
* distribuição de status;
* horários com mais acessos.

## Drill-down clicável 🖱️

Quando fizer sentido, valores no Ranking são clicáveis. Clicar em um domínio ou cliente aplica esse valor como filtro e atualiza o período.

Isso é útil quando você percebe um domínio muito frequente ou um cliente com atividade incomum.

## Totais podem diferir do Pi-hole ⚖️

O dashboard nativo do Pi-hole e o YAPD podem usar janelas de tempo levemente diferentes. O YAPD avalia o intervalo selecionado até o último minuto completo, então os totais podem diferir da tela nativa do Pi-hole para o mesmo dia aparente.

{% hint style="info" %}
📌 O Ranking usa apenas dados salvos localmente por importações do Overview. Ele não é uma tabela de queries ao vivo.
{% endhint %}
