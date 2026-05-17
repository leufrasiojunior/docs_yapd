---
description: Uma introdução simples ao que o YAPD faz por usuários de Pi-hole.
icon: house
---

# O que é o YAPD? 🧩

YAPD é um dashboard único para operar múltiplas instâncias Pi-hole v6+ sem precisar alternar entre vários painéis do Pi-hole.

## Por que ele existe 💡

Usar um Pi-hole é simples. Usar vários Pi-holes em casa, em um laboratório, em uma rede com VLANs ou em um pequeno escritório pode ficar bagunçado:

* configurações podem divergir entre instâncias;
* a atividade DNS fica espalhada em dashboards diferentes;
* mudanças importantes podem passar despercebidas;
* sync manual pode afetar o Pi-hole errado;
* falhas temporárias de conexão podem ser difíceis de entender.

O YAPD oferece um lugar central para observar, comparar e operar essas instâncias.

## O que o YAPD faz bem ✅

* 👀 **Visibilidade diária**: acompanhe métricas ao vivo e atividade DNS recente.
* 📊 **Análise histórica**: use o Overview para importar e analisar histórico de consultas.
* 🧱 **Gerenciamento de objetos do Pi-hole**: trabalhe com grupos, clientes, domínios e ad-lists.
* ⚙️ **Revisão de configuração**: compare tópicos de configuração do Pi-hole e identifique drift.
* 🔁 **Fluxos de sync**: copie estados selecionados de uma instância de origem para outros destinos.
* 🔔 **Acompanhamento operacional**: mantenha erros e eventos importantes visíveis em Notificações.

## O que o YAPD não é 🚫

O YAPD não substitui o entendimento do impacto de uma mudança no Pi-hole. Ele ajuda a operar com mais segurança, mas ações como apagar domínios, alterar grupos, sincronizar configurações ou apagar histórico do Overview ainda podem afetar sua rede.

{% hint style="warning" %}
🧪 O YAPD está em desenvolvimento. Tenha cuidado antes de aplicar mudanças em instâncias Pi-hole de produção.
{% endhint %}

## Para onde ir agora 🧭

* Nova instalação: [Instalar com Docker Compose](../administration/install-with-docker-compose.md)
* Primeiro login: [Primeiro acesso e setup](first-access-and-setup.md)
* Uso diário: [Dashboard](../daily-use/dashboard.md)
* Análise histórica: [Overview](../daily-use/overview.md)
