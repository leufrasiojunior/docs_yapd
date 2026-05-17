---
description: Revise dispositivos detectados pelo Pi-hole e gerencie grupos e tags de clientes.
icon: monitor-smartphone
---

# Clientes 📱

Clientes lista dispositivos de rede detectados pelas instâncias Pi-hole e ajuda a organizá-los com grupos, comentários e tags locais.

## O que você pode fazer 👀

Use Clientes para:

* pesquisar por cliente, IP ou endereço MAC;
* revisar onde um dispositivo está visível;
* inspecionar informações de primeira visualização e última query;
* editar tags locais;
* ocultar categorias de tags selecionadas da tabela;
* gerenciar associações de grupos;
* executar sync manual de clientes.

## Detalhes do cliente 🧾

A visão de detalhes pode mostrar:

* alias do cliente;
* endereço MAC;
* IPs detectados;
* fabricante do MAC;
* instância preferida;
* instâncias visíveis;
* grupos selecionados;
* comentários;
* contagem de queries por instância.

## Tags 🏷️

Tags são rótulos locais do YAPD. Use-as para organizar dispositivos sem alterar o Pi-hole.

Exemplos:

* `iot`;
* `kids`;
* `guest`;
* `work`;
* `ignore`.

## Grupos 👥

Associações de grupo do cliente usam a seleção de grupos baseada na baseline e depois aplicam mudanças nas instâncias gerenciadas disponíveis.

{% hint style="warning" %}
⚠️ Mudanças de grupo podem afetar o comportamento de filtragem do cliente selecionado. Confirme os grupos escolhidos antes de salvar.
{% endhint %}

## Disponibilidade parcial ⚠️

Se algumas instâncias com sync habilitado não puderem ser consultadas, o YAPD mostra os dados retornados pelas instâncias disponíveis e exclui as indisponíveis da tabela atual.
