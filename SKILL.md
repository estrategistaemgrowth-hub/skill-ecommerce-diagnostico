---
name: ecommerce-diagnostico
version: 2.0.0
description: Diagnóstico completo de ecommerce com arquitetura multi-agente. 8 agentes especializados rodam em paralelo — conversão, performance, SEO, catálogo, checkout, marketing, retenção e operação. Cada agente usa frameworks do Obsidian da Agência Mavi. Entrega score por dimensão, quick wins e plano 30/60/90 dias. Use sempre que o usuário mencionar: loja online com baixa conversão, abandono de carrinho, diagnóstico de ecommerce, auditoria de loja, por que minha loja não vende, análise de loja virtual, revisão de checkout, ou queira melhorar resultados em qualquer plataforma (Tray, NuvemShop, Shopify, WooCommerce, VTEX, Mercado Shops).
author: Agência Mavi
website: https://agenciamavi.com.br
license: MIT
compatibility: claude-code
allowed-tools:
  - Read
  - WebFetch
  - WebSearch
  - Agent
---

# Diagnóstico de Ecommerce — Orquestrador Multi-Agente

> Desenvolvido por **Agência Mavi** — Especialistas em crescimento para ecommerce.
> Versão 2.0.0 | 8 Agentes Especializados com base no Obsidian

---

## Arquitetura

```
Usuário
   ↓
Orquestrador (este arquivo)
   ↓ coleta contexto
   ↓ spawna 8 agentes em paralelo
   ↙  ↙  ↙  ↙  ↙  ↙  ↙  ↙
 CRO  Perf SEO  Cat  Chk  Mkt  CRM  Ops
   ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘
   ↓ consolida relatórios JSON
   ↓
Relatório Final Priorizado
```

Cada agente lê seus arquivos do Obsidian como base de conhecimento e retorna um JSON estruturado com score, problemas e quick wins para sua dimensão.

---

## Fase 1 — Coleta de Informações

Se o usuário não forneceu detalhes, faça estas perguntas em **no máximo 2 blocos**:

### Bloco A
1. Qual é a URL da loja?
2. Qual plataforma usa? (Tray, NuvemShop, Shopify, WooCommerce, VTEX, outro)
3. Qual o nicho e ticket médio? (ex: moda feminina R$150, suplementos R$80)
4. Qual a principal dor hoje? (baixa conversão, abandono de carrinho, pouco tráfego, outro)

### Bloco B (se não fornecidos)
5. Qual a taxa de conversão atual?
6. Principal fonte de tráfego? (Instagram, Google, orgânico, marketplace)
7. Ferramentas de analytics instaladas? (GA4, Pixel Meta, Hotjar)
8. Qual o faturamento mensal aproximado? (para calibrar prioridades)

Se URL disponível, use WebFetch para capturar o HTML da home e de uma página de produto antes de spawnar os agentes.

---

## Fase 2 — Spawn dos 8 Agentes em Paralelo

**IMPORTANTE:** Spawne TODOS os 8 agentes em uma única mensagem (chamadas simultâneas ao Agent tool) para que rodem em paralelo. Não aguarde um terminar para iniciar o próximo.

Passe para cada agente o seguinte contexto no prompt:

```
Contexto da loja:
- URL: [URL]
- Plataforma: [plataforma]
- Nicho: [nicho]
- Ticket médio: [ticket]
- Principal dor relatada: [dor]
- Taxa de conversão: [cvr ou "não informada"]
- Fonte de tráfego principal: [canal]
- HTML capturado: [html resumido ou "não disponível"]

Analise sua dimensão específica e retorne o JSON no formato definido no seu arquivo de instruções.
```

### Mapeamento dos Agentes

| Dimensão | Agente | Arquivo |
|----------|--------|---------|
| D1 — Conversão/CRO | ecommerce-agente-cro | `~/.claude/agents/ecommerce-agente-cro.md` |
| D2 — Performance | ecommerce-agente-performance | `~/.claude/agents/ecommerce-agente-performance.md` |
| D3 — SEO | ecommerce-agente-seo | `~/.claude/agents/ecommerce-agente-seo.md` |
| D4 — Catálogo | ecommerce-agente-catalogo | `~/.claude/agents/ecommerce-agente-catalogo.md` |
| D5 — Checkout | ecommerce-agente-checkout | `~/.claude/agents/ecommerce-agente-checkout.md` |
| D6 — Marketing | ecommerce-agente-marketing | `~/.claude/agents/ecommerce-agente-marketing.md` |
| D7 — Retenção | ecommerce-agente-retencao | `~/.claude/agents/ecommerce-agente-retencao.md` |
| D8 — Operação | ecommerce-agente-operacao | `~/.claude/agents/ecommerce-agente-operacao.md` |

---

## Fase 3 — Consolidação e Relatório Final

Após receber os JSONs de todos os 8 agentes, consolide no seguinte formato:

```
# Diagnóstico de Ecommerce — [Nome/URL da Loja]
Agência Mavi | Data: [data] | Versão 2.0 Multi-Agente

## Resumo Executivo
[2-3 frases sobre o estado geral. Qual é o maior gap? Qual é a maior oportunidade?]

## Score por Dimensão

| Dimensão              | Score | Status | Maior Problema |
|-----------------------|-------|--------|----------------|
| D1 Conversão/CRO      | X/10  | 🔴🟡🟢 | [resumo] |
| D2 Performance        | X/10  | 🔴🟡🟢 | [resumo] |
| D3 SEO/Visibilidade   | X/10  | 🔴🟡🟢 | [resumo] |
| D4 Catálogo/Produtos  | X/10  | 🔴🟡🟢 | [resumo] |
| D5 Checkout/Pagamento | X/10  | 🔴🟡🟢 | [resumo] |
| D6 Marketing/Tráfego  | X/10  | 🔴🟡🟢 | [resumo] |
| D7 Retenção/CRM       | X/10  | 🔴🟡🟢 | [resumo] |
| D8 Operação           | X/10  | 🔴🟡🟢 | [resumo] |
| **Score Geral**       | X/10  |        |                |

🔴 Crítico (0–4) | 🟡 Atenção (5–7) | 🟢 Bom (8–10)

---

## Problemas por Impacto

### Alto Impacto — Resolver em 30 dias
[Todos os problemas classificados como "alto" pelos agentes, priorizados por impacto financeiro]

### Médio Impacto — Resolver em 60 dias
[Problemas "médio" agregados]

### Baixo Impacto — Melhorias incrementais (90+ dias)
[Problemas "baixo" agregados]

---

## Quick Wins — Implementar Esta Semana
[Todos os quick_wins de todos os agentes, removendo duplicatas e priorizando por impacto]

1. [Ação] | Dimensão: [D?] | Impacto estimado: [X]
2. ...

---

## Plano de Ação

### Semana 1
- [ ] [Ação] | Responsável: lojista/dev/agência | Dimensão: D?

### Mês 1 (30 dias)
- [ ] [Ação prioritária]

### Mês 2 (60 dias)
- [ ] [Melhorias estruturais]

### Mês 3 (90 dias)
- [ ] [Otimizações de refinamento]

---

## Estimativa de Impacto Total
Se todos os problemas de Alto Impacto forem resolvidos:
- Conversão estimada: de X% para Y%
- Impacto na receita: +Z% aproximado
- Dimensão com maior ROI imediato: [D?]

---

*Diagnóstico gerado pelo sistema multi-agente da Agência Mavi.*
*Cada dimensão foi analisada por um agente especializado com base em frameworks proprietários.*
*Para implementação assistida: agenciamavi.com.br*
```

---

## Regras do Orquestrador

1. **Sempre spawnar os 8 agentes em paralelo** — nunca sequencialmente
2. **Consolidar com síntese real** — não apenas listar os JSONs, mas interpretar e priorizar
3. **Impacto financeiro em foco** — cada problema deve ter estimativa de ganho em receita ou conversão
4. **Quick wins primeiro** — o lojista precisa ver resultado rápido
5. **Adaptar ao porte** — prioridades de R$30k/mês são diferentes de R$500k/mês
6. **Citar o framework** — quando recomendar algo do Obsidian, mencionar o framework (ex: "Aplicando StoryBrand...")
