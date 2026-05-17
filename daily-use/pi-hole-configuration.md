---
description: Revise tópicos de configuração do Pi-hole, detecte drift, baixe Teleporter ZIP e sincronize ajustes.
icon: settings-2
---

# Configurações do Pi-hole ⚙️

Configurações permite editar ajustes detalhados do Pi-hole por tópico, detectar drift, baixar um Teleporter ZIP e sincronizar tópicos selecionados entre instâncias.

![Configurações do YAPD](../.gitbook/assets/screenshots/configuration.png)

## Tópicos 🧭

A tela Configurações é organizada em abas como:

* DNS;
* DHCP;
* NTP;
* Resolver;
* Database;
* Webserver;
* Files;
* Misc;
* Debug.

## Instância de origem 🎯

Escolha a instância de origem no topo da tela. Edições na aba ativa são aplicadas à instância de origem selecionada.

## Edição de campos ✏️

Campos podem ser:

* toggles booleanos;
* valores de texto;
* valores em formato JSON para configurações estruturadas.

O YAPD mostra metadados úteis, como caminho do campo, tipo, padrão, valores permitidos e flags.

## Detecção de drift 🧭

Se um tópico difere entre instâncias, o YAPD mostra um aviso de drift. Use os links do aviso para ir diretamente à aba e ao campo afetado.

## Ignorar sync 🙈

Use **Ignore sync** quando um campo é intencionalmente diferente entre instâncias. Campos ignorados saem dos avisos de drift até serem restaurados.

## Sincronizar uma aba 🔁

Use **Sync** dentro de um tópico para copiar a configuração daquela aba de uma origem selecionada para destinos selecionados.

{% hint style="warning" %}
⚠️ Sync de configuração pode mudar o comportamento do Pi-hole. Revise origem, destinos e aba antes de confirmar.
{% endhint %}

## Teleporter ZIP 📦

Use **Baixar Teleporter ZIP** para baixar uma exportação Teleporter do Pi-hole a partir da origem de configuração atual.
