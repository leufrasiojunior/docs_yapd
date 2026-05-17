---
description: Orientações práticas de segurança para usar o YAPD com instâncias Pi-hole reais.
icon: triangle-alert
---

# Operação segura 🛡️

O YAPD pode ler e alterar estado real do Pi-hole. Revise as ações antes de confirmar.

## Bons hábitos ✅

* 👀 Leia a confirmação antes de apagar ou sincronizar.
* 🎯 Confirme origem e instâncias de destino.
* 👑 Saiba qual instância é a baseline.
* 🔁 Use sync de forma intencional, não como botão de "corrigir tudo".
* 🔔 Confira Notificações depois de operações com falha parcial.
* 🧪 Teste conexões de instâncias depois de mudar senhas, URLs, certificados ou proxies.
* 💾 Mantenha backups fora do YAPD.

## Ações que pedem cuidado extra ⚠️

| Ação | Por que importa |
| --- | --- |
| Apagar grupos, domínios ou ad-lists | Remove dados de instâncias gerenciadas. |
| Sincronizar grupos, domínios, ad-lists, clientes ou configuração | Copia o estado selecionado para instâncias de destino. |
| Trocar a instância primária | Altera a referência de baseline usada globalmente pelo YAPD. |
| Apagar períodos do Overview | Remove histórico local salvo para aquele período. |
| Alternar estado de bloqueio | Pode mudar o comportamento de filtragem DNS em um ou mais Pi-holes. |

## Certificados 🔐

Se um Pi-hole usa certificado autoassinado, permita explicitamente apenas quando você confia naquela instância e naquele caminho de rede. Se você tem uma CA privada, prefira adicionar a CA customizada em vez de aceitar certificados desconhecidos de forma ampla.

## Sessões 🔑

Se uma instância mostra erros de sessão, use **Reauthenticate** ou edite a credencial da instância. Não assuma que todas as instâncias usam a mesma senha, a menos que você tenha configurado isso.

## Aviso beta 🚧

O YAPD ainda está em desenvolvimento ativo. Quando possível, use primeiro em um ambiente controlado e depois expanda para instâncias Pi-hole mais importantes quando você já conhecer os fluxos.
