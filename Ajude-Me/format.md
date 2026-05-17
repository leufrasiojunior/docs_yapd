# 🛠️ Dashboard de Monitoramento YAPD

Bem-vindo ao guia de documentação técnica do projeto. Este documento serve como um teste completo de renderização Markdown.

---

## 📈 Status de Performance

Abaixo, uma tabela comparativa do desempenho das instâncias:

| Instância | Status | Latência | Carga de CPU | Memória |
| :--- | :--- | :--- | :--- | :--- |
| **Node-01** | ✅ Online | 12ms | 5% | 128MB |
| **Node-02** | ⚠️ Alerta | 85ms | 42% | 512MB |
| **Proxy-Edge** | ❌ Offline | -- | -- | -- |

---

## 🖼️ Galeria de Testes

Abaixo, uma imagem de exemplo para validação de carregamento:

![Exemplo de Placeholder](https://via.placeholder.com/600x200.png?text=Imagem+de+Teste+Markdown)

---

## 💻 Exemplos de Código

### 1. Configuração do Ambiente (`.env`)
```env
PORT=3000
DB_PATH=./data/persistence.json
LOG_LEVEL=debug
```

### 2. Lógica de Persistência (NestJS/TS)
O sistema prioriza a escrita direta em arquivos JSON para evitar perda de dados:

```typescript
import { Injectable } from '@nestjs/common';
import * as fs from 'fs/promises';

@Injectable()
export class StorageService {
  private readonly filePath = './data/config.json';

  async saveData(data: any): Promise<void> {
    try {
      const jsonContent = JSON.stringify(data, null, 2);
      await fs.writeFile(this.filePath, jsonContent, 'utf-8');
      console.log('Dados salvos com sucesso em JSON.');
    } catch (error) {
      console.error('Erro ao salvar persistência:', error);
    }
  }
}
```

---

## ⚙️ Configuração Docker Compose

Exemplo de mapeamento de volumes para persistência local em ambiente WSL:

```yaml
version: '3.8'
services:
  app-server:
    image: yapd-dashboard:latest
    ports:
      - "3000:3000"
    volumes:
      - ./data:/usr/src/app/data
      - /mnt/c/Users/User/AppData/Local:/config/windows
    environment:
      - NODE_ENV=production
```

---

## 🧪 Notas de Laboratório

> **Aviso:** Nunca utilize `localStorage` para configurações críticas que precisem de persistência entre diferentes dispositivos ou sessões do navegador.

1. [x] Implementar parser de JSON.
2. [x] Validar volumes Docker no WSL.
3. [ ] Criar interface de tradução i18n.