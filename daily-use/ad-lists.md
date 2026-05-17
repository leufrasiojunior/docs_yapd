---
description: Gerencie ad-lists do Pi-hole e mantenha-as sincronizadas entre instâncias.
icon: list
---

# Ad-lists 🧾

Ad-lists gerencia fontes de lista já cadastradas no Pi-hole e ajuda a mantê-las sincronizadas entre instâncias.

![Ad-lists do YAPD](../.gitbook/assets/screenshots/ad-lists.png)

## O que você pode fazer ✅

Use Ad-lists para:

* adicionar listas de block ou allow;
* pesquisar por endereço ou comentário;
* ativar ou desativar listas;
* editar comentários e grupos;
* remover uma ou mais listas;
* revisar status de sync;
* sincronizar listas manualmente entre instâncias.

## Criar uma lista ➕

Ao criar uma lista, informe:

* endereço;
* comentário;
* grupos.

O YAPD replica a configuração entre as instâncias gerenciadas sempre que possível.

## Editar uma lista ✏️

O diálogo de edição mostra detalhes gerais e associações de grupo. Salve mudanças somente depois de confirmar grupos e status selecionados.

## Sync pendente 🔁

Se uma lista estiver ausente em uma ou mais instâncias, o YAPD marca como sync pendente. Use o diálogo de sync para escolher origem e instâncias de destino.

{% hint style="warning" %}
⚠️ Remover uma ad-list pode alterar o comportamento de filtragem para clientes associados aos grupos dela.
{% endhint %}
