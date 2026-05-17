---
description: Resolva os problemas mais comuns de instalação e uso do YAPD.
icon: life-ring
---

# Problemas comuns 🧯

Esta página lista sintomas visíveis ao usuário e o que conferir primeiro.

## O login funciona, mas volta para a tela de login 🔁

Causa provável: cookie ou origem pública não batem.

Confira:

* `WEB_ORIGIN` corresponde exatamente à URL do navegador.
* `COOKIE_SECURE=true` quando o acesso é HTTPS.
* `COOKIE_SECURE=false` somente quando o acesso é HTTP simples.
* O proxy reverso encaminha o protocolo original com `X-Forwarded-Proto`.

## O YAPD não alcança um Pi-hole 🌐

Confira:

* URL, protocolo, porta e caminho do Pi-hole;
* se o container do YAPD alcança essa rede;
* se um firewall bloqueia o caminho;
* se a senha ou application password do Pi-hole mudou;
* se a instância usa certificado autoassinado.

Use **Instâncias > Test** depois de fazer alterações.

## Erro de certificado autoassinado 🔐

Se o Pi-hole usa certificado autoassinado local, edite a instância e:

* permita explicitamente o certificado autoassinado; ou
* informe o bundle da CA customizada.

Faça isso somente para endpoints Pi-hole em que você confia.

## Notificações push não ativam 🔔

Push precisa de contexto seguro no navegador.

Confira:

* você está usando HTTPS com certificado confiável, ou `localhost`;
* o navegador não bloqueou notificações para o site;
* o proxy não faz cache de `/notifications-sw.js`;
* a configuração de push está disponível no servidor.

## Overview não mostra dados 📊

O Overview usa dados históricos armazenados localmente. Ele não mostra automaticamente dados ao vivo do Pi-hole se um período histórico ainda não foi importado.

Vá para **Overview > Período e cobertura**, escolha um dia fechado e solicite uma importação. Depois acompanhe em **Overview > Jobs**.

## Overview não permite importar hoje 📅

Isso é esperado. Importações manuais do Overview são limitadas a um dia fechado. Escolha ontem ou uma data anterior.

## O live mode do Queries Log para quando o modo disk é ativado 💿

Isso é esperado. O modo on-disk é mais lento e serve para dados mais antigos do Pi-hole, então atualizações ao vivo são desativadas.

## Um sync teve sucesso parcial ⚠️

Abra **Notificações** e revise a falha. Depois confira a instância afetada em **Instâncias**.

Causas comuns:

* uma instância de destino estava offline;
* uma sessão expirou;
* credenciais mudaram;
* validação TLS falhou;
* uma resposta do Pi-hole veio diferente do esperado.

## O container aparece como unhealthy 🐳

Confira container e logs:

```bash
docker compose ps
docker compose logs --tail=200 yapd
docker compose logs --tail=200 postgres
```

Um Pi-hole externo inalcançável deve ser tratado como problema de instância, não como motivo para alterar dados manualmente sem checar logs do YAPD e Notificações.
