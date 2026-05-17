---
description: Coloque o YAPD atrás de um proxy reverso e mantenha a segurança do navegador funcionando.
icon: shield-check
---

# Proxy reverso e HTTPS 🔐

Use um proxy reverso quando quiser um domínio amigável, certificado HTTPS confiável e recursos do navegador como notificações push.

## Caminho recomendado 🌐

Use este fluxo:

```text
Navegador -> https://yapd.exemplo.com -> proxy reverso -> http://HOST_YAPD:48080
```

A URL pública do navegador deve usar HTTPS. O caminho privado do proxy até o YAPD pode usar HTTP na porta `48080`.

{% hint style="warning" %}
⚠️ Evite usar `https://HOST_YAPD:48443` como upstream normal. Essa porta usa o certificado autoassinado interno do YAPD e costuma causar problemas de confiança no proxy.
{% endhint %}

## Configurações obrigatórias ⚙️

Defina estes valores no Compose:

```yaml
WEB_ORIGIN: "https://yapd.exemplo.com"
COOKIE_SECURE: "true"
NEXT_PUBLIC_API_BASE_URL: /api
INTERNAL_API_BASE_URL: http://127.0.0.1:3001/api
```

`WEB_ORIGIN` deve corresponder exatamente à URL que os usuários digitam no navegador.

## Exemplo com Nginx 🧱

```nginx
server {
    listen 443 ssl;
    server_name yapd.exemplo.com;

    ssl_certificate /caminho/para/fullchain.pem;
    ssl_certificate_key /caminho/para/privkey.pem;

    location / {
        proxy_pass http://HOST_YAPD:48080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_read_timeout 86400;
    }
}
```

## Exemplo com Caddy ⚡

```caddy
yapd.exemplo.com {
    reverse_proxy http://HOST_YAPD:48080 {
        header_up Host {host}
        header_up X-Real-IP {remote_host}
        header_up X-Forwarded-For {remote_host}
        header_up X-Forwarded-Proto {scheme}
    }
}
```

## Checklist para Nginx Proxy Manager ✅

1. Crie um novo **Proxy Host**.
2. Defina **Domain Names** com o domínio do YAPD.
3. Defina **Scheme** como `http`.
4. Defina **Forward Hostname/IP** com o host do YAPD.
5. Defina **Forward Port** como `48080`.
6. Ative **Websockets Support**.
7. Adicione ou solicite um certificado SSL confiável.
8. Ative **Force SSL** depois de confirmar que o domínio funciona.
9. Mantenha **Cache Assets** desativado enquanto testa notificações push.

## Notificações push 🔔

Push no navegador precisa de HTTPS com certificado público confiável. Um certificado autoassinado normalmente bloqueia o service worker e impede o push.

Se o proxy faz cache de assets, crie uma regra sem cache para:

```text
/notifications-sw.js
```

Veja [Notificações](../daily-use/notifications.md) para o comportamento no produto.
