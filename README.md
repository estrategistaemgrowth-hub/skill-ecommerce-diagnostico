# 🛒 Ecommerce Diagnóstico — Claude Code Skill

> Skill para **Claude Code** desenvolvida pela [Agência Mavi](https://agenciamavi.com.br).  
> Diagnóstico completo de lojas virtuais com score por dimensão, quick wins e plano de ação.

---

## O que faz

Analisa **8 dimensões críticas** de qualquer loja virtual e entrega um relatório priorizado:

| # | Dimensão | O que analisa |
|---|----------|---------------|
| D1 | Conversão / CRO | Hero, CTAs, prova social, trust signals, urgência |
| D2 | Performance técnica | LCP, CLS, imagens, scripts, CDN |
| D3 | SEO e visibilidade | Titles, schema, URLs, sitemap, canonicals |
| D4 | Catálogo e produtos | Fotos, descrições, variantes, avaliações |
| D5 | Checkout e pagamento | Etapas, Pix, parcelamento, SSL, abandono |
| D6 | Marketing e tráfego | Pixels, GA4, remarketing, UTMs, Shopping |
| D7 | Retenção e CRM | E-mail flows, WhatsApp, fidelidade, NPS |
| D8 | Operação | Frete, devolução, atendimento, FAQ |

**Output:** score 0–10 por dimensão, quick wins da semana, plano 30/60/90 dias.

**Plataformas suportadas:** Tray · NuvemShop · Shopify · WooCommerce · VTEX · Mercado Shops

---

## Instalação

### Passo 1 — Copie os arquivos para o Claude Code

```bash
# Clone o repositório
git clone https://github.com/agenciamavi/claude-skills.git

# Copie a skill para o diretório do Claude Code
cp -r claude-skills/ecommerce-diagnostico ~/.claude/skills/

# Copie o command
cp claude-skills/ecommerce-diagnostico/command.md ~/.claude/commands/ecommerce-diagnostico.md
```

### Passo 2 — Reinicie o Claude Code

Feche e abra novamente o Claude Code. A skill aparecerá na lista de skills disponíveis.

### Instalação manual (sem git)

1. Baixe os arquivos `SKILL.md` e `command.md` deste repositório
2. Crie a pasta `~/.claude/skills/ecommerce-diagnostico/`
3. Coloque o `SKILL.md` dentro dela
4. Copie o `command.md` para `~/.claude/commands/ecommerce-diagnostico.md`

---

## Como usar

Depois de instalado, basta digitar no Claude Code:

```
/ecommerce-diagnostico
```

Ou mencionar naturalmente:

> *"preciso de um diagnóstico da minha loja"*  
> *"minha loja tem baixa conversão, pode analisar?"*  
> *"por que meu ecommerce não vende?"*

A skill dispara automaticamente nesses contextos.

---

## Exemplo de output

```
# Diagnóstico de Ecommerce — minhaloja.com.br

## Score por Dimensão

| Dimensão              | Score | Status |
|-----------------------|-------|--------|
| D1 Conversão/CRO      |  4/10 | 🔴     |
| D2 Performance        |  6/10 | 🟡     |
| D3 SEO/Visibilidade   |  5/10 | 🟡     |
| D4 Catálogo/Produtos  |  7/10 | 🟢     |
| D5 Checkout/Pagamento |  3/10 | 🔴     |
| D6 Marketing/Tráfego  |  5/10 | 🟡     |
| D7 Retenção/CRM       |  2/10 | 🔴     |
| D8 Operação           |  6/10 | 🟡     |
| Score Geral           |  4.8/10 |      |

## Quick Wins (esta semana)
- [ ] Ativar e-mail de carrinho abandonado (impacto: +15% receita)
- [ ] Adicionar Pix como opção de pagamento
- [ ] Exibir parcelamento em 12x na página do produto
...
```

---

## Autor

Desenvolvido por **Agência Mavi**  
Especialistas em crescimento para ecommerce brasileiro.

- 🌐 [agenciamavi.com.br](https://agenciamavi.com.br)
- 📧 contato@agenciamavi.com.br

---

## Licença

MIT — Livre para usar, modificar e distribuir com atribuição ao autor original.
