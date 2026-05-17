---
description: Pesquise atividade DNS recente e aplique ações em domínios a partir de um só lugar.
icon: file-text
---

# Queries Log 🔎

Queries Log mostra consultas DNS recentes no escopo selecionado do YAPD, com filtros, sugestões, atualização ao vivo e ações rápidas de domínio.

![Queries Log do YAPD](../.gitbook/assets/screenshots/queries.png)

## O que você pode filtrar 🧰

Use filtros para reduzir a tabela por:

* intervalo de tempo;
* domínio;
* IP do cliente;
* grupos;
* upstream;
* tipo;
* status;
* resposta;
* DNSSEC;
* modo de banco em disco.

Os filtros de data usam o fuso horário da aplicação.

## Modo live ⚡

O modo live atualiza a tabela de queries a cada poucos segundos. Desative o live mode quando quiser navegar entre páginas com calma.

## Modo on-disk 💿

Use **Carregar do banco em disco** quando precisar de dados mais antigos do Pi-hole.

{% hint style="warning" %}
🐢 O modo on-disk é mais lento e desativa atualizações ao vivo.
{% endhint %}

## Ações rápidas de domínio 🛠️

Na tabela de queries, você pode usar ações como:

* bloquear um domínio;
* bloquear por regex;
* permitir um domínio.

O YAPD aplica a ação nas instâncias disponíveis e informa falhas parciais quando algumas instâncias não puderem ser atualizadas.

## Aviso de revisão de grupos 🧭

Se o YAPD avisar que uma revisão de grupos é necessária, abra **Grupos**. Isso mantém filtros de query por grupo corretos entre instâncias.
