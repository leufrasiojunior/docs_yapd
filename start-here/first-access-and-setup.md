---
description: Conclua o primeiro setup do YAPD e faça login pela primeira vez.
icon: rocket
---

# Primeiro acesso e setup 🚀

O assistente de setup cria a baseline inicial do Pi-hole, cadastra suas primeiras instâncias, escolhe o modo de login e salva suas preferências visuais.

## Antes de começar 📋

Tenha em mãos:

* a URL ou o IP de cada Pi-hole que você quer gerenciar;
* a senha do Pi-hole ou application password de cada instância;
* a instância que será usada como **master** ou **baseline**;
* se o Pi-hole usa HTTP, HTTPS, certificado confiável ou certificado autoassinado;
* o fuso horário que o YAPD deve usar para datas e relatórios.

## Conclua o assistente 🪄

{% stepper %}
{% step %}
### Abra o YAPD 🌐

Abra o endereço do YAPD no navegador. Com a instalação padrão por Compose, o acesso direto costuma ser `http://<ip-do-servidor>:48080`.
{% endstep %}

{% step %}
### Cadastre os Pi-holes 🧱

Adicione uma ou mais URLs de Pi-hole. Em cada linha, informe alias, protocolo, host, porta ou caminho quando necessário, e a senha ou application password.
{% endstep %}

{% step %}
### Escolha o Pi-hole master 👑

Selecione o Pi-hole que será a baseline oficial do YAPD. A baseline é a principal referência para login e para várias comparações de sync.
{% endstep %}

{% step %}
### Escolha o modo de login 🔐

Escolha se os operadores vão entrar com a senha do Pi-hole master ou com uma senha dedicada do YAPD criada durante o setup.
{% endstep %}

{% step %}
### Defina preferências visuais 🎛️

Escolha idioma da aplicação, fuso horário, tema, fonte, largura da página, comportamento da navbar e estilo da sidebar.
{% endstep %}

{% step %}
### Finalize o setup ✅

Revise as escolhas e conclua o assistente. O YAPD valida as conexões com os Pi-holes antes de salvar o setup.
{% endstep %}
{% endstepper %}

## Modos de login 🔑

| Modo | O que significa | Quando usar |
| --- | --- | --- |
| **Senha do Pi-hole master** | O YAPD usa o fluxo oficial de login do Pi-hole v6 pelo Pi-hole master. | Quando você quer que o login humano siga a senha do Pi-hole. |
| **Senha do YAPD** | O YAPD salva uma senha do produto em hash para login humano. | Quando você quer que operadores entrem sem usar a senha do Pi-hole. |

{% hint style="info" %}
🔒 Credenciais técnicas do Pi-hole são salvas criptografadas para que o backend opere as instâncias registradas. A senha digitada no login não é salva como senha em texto puro.
{% endhint %}

## Se o setup falhar 🧯

Confira as causas mais comuns:

* a URL do Pi-hole inclui o protocolo duas vezes;
* host, porta ou caminho estão incorretos;
* senha ou application password estão incorretos;
* o backend não consegue alcançar o Pi-hole pela rede do Docker;
* o Pi-hole usa certificado autoassinado e você não permitiu isso explicitamente;
* o Pi-hole master selecionado ficou incompleto.

Para recuperação, veja [Problemas comuns](../troubleshooting/common-problems.md).
