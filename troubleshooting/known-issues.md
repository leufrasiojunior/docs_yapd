---
description: Limitações e pontos conhecidos para manter em mente.
icon: bug
---

# Erros conhecidos 🐞

O YAPD é um software em evolução. Estes são comportamentos e limitações que vale lembrar.

## Alcance intermitente do Pi-hole 🌐

Às vezes o YAPD pode perder conexão com uma instância Pi-hole, não conseguir localizá-la ou exibir rapidamente que ela está inalcançável. Em alguns casos, a instância se recupera pouco depois sem reinício manual.

O que fazer:

* aguarde um pouco e atualize a tela afetada;
* confira **Instâncias** para ver o último erro;
* teste a conexão da instância;
* revise **Notificações** para entender o motivo com mais clareza;
* colete logs se o problema se repetir.

## Overview depende de histórico importado 📊

O Overview pode parecer vazio depois de uma instalação nova porque ele analisa apenas dados salvos no banco local do YAPD. Importe um dia fechado antes de esperar rankings ou gráficos.

## Modo on-disk de queries é mais lento 💿

O Queries Log pode consultar dados mais antigos no banco em disco do Pi-hole, mas esse modo é mais lento e desativa atualizações ao vivo.

## Push exige HTTPS real 🔔

Notificações push normalmente não funcionam por acesso HTTP direto via IP ou por certificados públicos autoassinados no navegador. Use um domínio HTTPS confiável.

## Alguns fluxos ainda estão evoluindo 🚧

O roadmap do YAPD inclui backup mais forte, visibilidade operacional em tempo real, diagnósticos melhores de saúde e futuros recursos de controle parental. Leve os avisos beta a sério ao operar instâncias Pi-hole de produção.
