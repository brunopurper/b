# Technique Eletrônica — Sistema de Gestão de Orçamentos

**Data:** 2026-05-07  
**Tipo:** HTML único (sem servidor)  
**Tema:** Dark moderno

---

## Visão Geral

Arquivo único `index.html` que substitui o sistema antigo do pai. Funciona offline, abre direto no navegador, dados persistidos em `localStorage`.

## Módulos

### 1. Orçamento (Budget Robot)
- Campos: Nome do cliente, Aparelho, Diagnóstico (textarea), Valor à vista, Parcelas (dropdown), Celular
- Preview ao vivo da mensagem WhatsApp à direita do formulário
- Valor parcelado calculado automaticamente com base nas taxas configuradas
- Envio via `wa.me` com mensagem pré-formatada
- Salva no histórico ao enviar

**Mensagem gerada:**
```
Olá, *{Nome}*! 👋

Identificamos o problema no seu *{Aparelho}*.

*Diagnóstico:* {Diagnóstico}

*Investimento:*
💵 À vista: R$ {valor}
💳 Parcelado: Até {n}x de R$ {parcela}

Podemos dar continuidade no serviço?
```

### 2. Aparelho Pronto
- Campos: Nome do cliente, Aparelho, Celular
- Envio via WhatsApp com mensagem de notificação

**Mensagem gerada:**
```
Olá, *{Nome}*! 😊

Seu *{Aparelho}* está pronto para retirada! ✅

Aguardamos você em nossa loja.

Technique Eletrônica 🔧
```

### 3. Calculadora de Taxas (bidirecional)
- Toggle entre dois modos:
  - **Quanto cobrar?** → digita valor desejado líquido → exibe valor a cobrar por modalidade
  - **Quanto recebo?** → digita valor cobrado → exibe valor líquido por modalidade
- Tabela com todas as modalidades: Débito, 1x–12x crédito

### 4. Histórico
- Lista de orçamentos enviados (data, cliente, aparelho, valor)
- Reenvio via WhatsApp
- Filtro por nome/data
- Botão limpar histórico

### 5. Configurações de Taxas
- Tabela editável com taxa % por modalidade
- Valores padrão: Débito 1.5%, 1x 2.5%, 2x 3.5% ... 12x 12%
- Salvo em localStorage

## Arquitetura

- **Tecnologia:** HTML5 + CSS3 + JavaScript vanilla
- **Dependências CDN:** Fonte Inter (Google Fonts), ícones Lucide
- **Persistência:** localStorage (histórico, taxas)
- **Tema:** Dark (#0f0f0f fundo, #1a1a1a cards, #22c55e verde destaque)
- **Layout:** Sidebar lateral fixa + área de conteúdo principal
