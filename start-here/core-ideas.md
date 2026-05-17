---
description: Entenda as ideias de produto que aparecem em várias telas do YAPD.
icon: lightbulb
---

# Ideias principais 💡

O YAPD usa alguns conceitos recorrentes em suas telas.

## Instância 🧱

Uma **instância** é um Pi-hole cadastrado no YAPD. Instâncias podem ser testadas, editadas, reautenticadas, incluídas no sync ou removidas de operações globais de sync.

## Baseline 👑

A **baseline** é o Pi-hole principal de referência. O YAPD usa essa instância como autoridade principal para várias comparações e fluxos de sync. Você pode trocar a instância primária pela tela **Instâncias**.

## Escopo 🎯

Algumas telas permitem escolher um escopo:

* **Todas as instâncias**: o YAPD agrega ou compara todas as instâncias disponíveis.
* **Uma instância**: o YAPD mostra apenas um Pi-hole.

## Sync 🔁

Sync copia dados selecionados de uma origem para uma ou mais instâncias de destino. Ele pode se aplicar a grupos, clientes, domínios, ad-lists, tópicos de configuração ou estado de bloqueio.

{% hint style="warning" %}
⚠️ Revise origem e destinos antes de confirmar um sync. Sync é uma operação real contra suas instâncias Pi-hole.
{% endhint %}

## Drift ou divergência 🧭

Drift significa que uma instância não corresponde ao estado esperado ou à origem selecionada. O YAPD destaca divergências para que você revise antes de alterar algo.

## Histórico do Overview 📊

O Overview não lê apenas o dashboard ao vivo do Pi-hole. Ele usa histórico de consultas salvo no banco local do YAPD. Você precisa importar um dia fechado antes que o Overview consiga ranquear domínios, clientes, upstreams e status desse período.

## Notificações 🔔

Notificações são eventos e falhas armazenados. Elas ajudam a notar erros de conexão, falhas de sync, resultados de importação do Overview e outras mensagens operacionais.

## Status beta 🚧

O YAPD ainda está evoluindo. O produto exibe um aviso BETA porque pode operar diretamente em instâncias Pi-hole e porque alguns fluxos ainda estão sendo refinados.
