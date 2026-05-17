---
description: Guia do usuário para instalar, configurar e usar o YAPD com Pi-hole v6+.
icon: hand-wave
---

# Bem-vindo ao YAPD 👋

![Logo do YAPD](.gitbook/assets/brand/logo-bg-transparent.png)

YAPD é um dashboard auto-hospedado para quem usa mais de uma instância Pi-hole e quer operar tudo de forma mais clara e segura em um só lugar.

O YAPD é um projeto independente de terceiros. Ele não é afiliado, endossado nem patrocinado pela Pi-hole, LLC; "Pi-hole" é mencionado apenas para identificar compatibilidade com instalações Pi-hole.

Use esta documentação para instalar o YAPD, concluir o primeiro setup, entender cada tela, resolver erros comuns e usar a tela especial **Overview** para análise histórica de DNS.

{% hint style="warning" %}
🚧 O YAPD ainda está em desenvolvimento ativo. Trate-o como uma ferramenta operacional em fase inicial, especialmente ao usar com instâncias Pi-hole de produção.
{% endhint %}

## Comece por aqui 🌱

<table data-view="cards"><thead><tr><th></th><th data-type="content-ref"></th><th data-type="content-ref"></th></tr></thead><tbody><tr><td><h4>🚀 Novos usuários</h4></td><td><a href="start-here/what-is-yapd.md">what-is-yapd.md</a></td><td><a href="start-here/first-access-and-setup.md">first-access-and-setup.md</a></td></tr><tr><td><h4>🧭 Operação diária</h4></td><td><a href="daily-use/dashboard.md">dashboard.md</a></td><td><a href="daily-use/overview.md">overview.md</a></td></tr><tr><td><h4>🛠️ Administração</h4></td><td><a href="administration/install-with-docker-compose.md">install-with-docker-compose.md</a></td><td><a href="administration/reverse-proxy-and-https.md">reverse-proxy-and-https.md</a></td></tr><tr><td><h4>🧯 Algo quebrou</h4></td><td><a href="troubleshooting/common-problems.md">common-problems.md</a></td><td><a href="troubleshooting/known-issues.md">known-issues.md</a></td></tr></tbody></table>

## O que o YAPD ajuda você a fazer ✨

* 👀 Ver a atividade consolidada das suas instâncias Pi-hole.
* 🧱 Comparar e gerenciar grupos, clientes, domínios e ad-lists com mais facilidade.
* 🧭 Escolher um escopo global ou inspecionar um Pi-hole por vez.
* 🕵️ Revisar consultas recentes em **Queries Log**.
* 📊 Importar e analisar dados históricos no **Overview**.
* 🔔 Acompanhar falhas operacionais e mensagens do Pi-hole em **Notificações**.
* ⚙️ Revisar tópicos de configuração do Pi-hole e sincronizar ajustes selecionados.
* 🧪 Testar e reautenticar instâncias quando credenciais, certificados ou caminhos de rede mudarem.

## Telas principais 🖥️

![Print do Dashboard do YAPD](.gitbook/assets/screenshots/dashboard.png)

A sidebar do YAPD é organizada em **Overview**, **Operações** e **Status**:

* **Overview** (`/overview`): análise histórica armazenada no YAPD.
* **Dashboard** (`/dashboard`): métricas consolidadas e ao vivo do Pi-hole.
* **Queries Log** (`/queries`): atividade DNS recente e ações rápidas de domínio.
* **Grupos** (`/groups`), **Clientes** (`/clients`), **Domínios** (`/domains`), **Ad-lists** (`/lists`): objetos do Pi-hole gerenciados entre instâncias.
* **Instâncias** (`/instances`): cadastro, testes, reautenticação e comportamento de baseline.
* **Configurações** (`/config`): ajustes do Pi-hole por tópico, exportação Teleporter, detecção de drift e sync.
* **Notificações** (`/notifications`): eventos salvos, falhas e controles de notificação push.
