---
description: Crie, edite, sincronize e inspecione grupos do Pi-hole entre instâncias gerenciadas.
icon: waypoints
---

# Grupos 👥

Grupos é onde você gerencia grupos do Pi-hole a partir de uma visão consolidada do YAPD.

![Grupos do YAPD](../.gitbook/assets/screenshots/groups.png)

## O que você pode fazer ✅

Use Grupos para:

* criar um ou mais grupos;
* pesquisar grupos cadastrados;
* ativar ou desativar grupos;
* editar nomes e comentários;
* apagar grupos selecionados;
* sincronizar grupos ausentes para instâncias de destino;
* ver clientes vinculados a um grupo;
* gerenciar associação de clientes individualmente ou em lote.

## Criar grupos ➕

Novos grupos são criados ativos por padrão e sincronizados entre instâncias gerenciadas.

Você pode criar vários grupos separando nomes por espaços ou vírgulas. Use aspas para nomes com espaço, como `"Dispositivos Crianças"`.

## Sync pendente 🔁

Se um grupo existe em algumas instâncias, mas não em outras, o YAPD marca como sync pendente.

Abra o diálogo de sync para escolher:

* instância de origem;
* instâncias de destino;
* se deseja aplicar apenas um grupo ou todos os grupos pendentes.

## Grupos protegidos 🛡️

O YAPD pode marcar grupos padrão do sistema como protegidos. Trate esses grupos com cuidado extra porque o Pi-hole pode depender deles.

## Clientes vinculados 🔗

Use **Ver clientes** para inspecionar clientes associados a um grupo e ajustar associações individualmente ou em lote.
