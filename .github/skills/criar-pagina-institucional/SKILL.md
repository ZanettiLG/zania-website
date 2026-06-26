---
name: criar-pagina-institucional
description: 'Cria novas páginas institucionais seguindo o padrão visual do site Zan.IA. Use quando: precisar adicionar landing pages, páginas de serviço, páginas institucionais, ou seções que sigam o design system existente (glass panels, paleta Material Design 3, tipografia Space Grotesk/Geist/JetBrains Mono).'
argument-hint: 'Descrição da página a criar (ex: "página de preços", "landing page do serviço de chatbots")'
---

# Criar Página Institucional — Zan.IA

Gera uma nova página HTML seguindo o design system e convenções visuais do site Zan.IA.

## Quando Usar
- Adicionar novas landing pages ao site
- Criar páginas de serviço (ex: "Agentes de IA", "Fábrica de Mídia")
- Adicionar seções institucionais (ex: "Política de Privacidade", "Termos de Uso")
- Qualquer página que precise seguir o padrão visual existente

## Design System

### Design Tokens (CSS Variables)
```css
/* Cores - Material Design 3 */
--color-surface: #0c1324;
--color-surface-container: #191f31;
--color-surface-container-lowest: #070d1f;
--color-primary: #baf2ff;
--color-primary-container: #00e0ff;
--color-on-surface: #dce1fb;
--color-on-primary: #00363f;
--color-on-primary-container: #005f6d;
--color-outline-variant: #3b494c;

/* Fontes */
--font-display: 'Space Grotesk', sans-serif;
--font-body: 'Geist', sans-serif;
--font-code: 'JetBrains Mono', monospace;

/* Espaçamentos */
--spacing-gutter: 24px;
--spacing-margin-mobile: 16px;
--spacing-margin-desktop: 64px;
--spacing-base: 8px;
```

### Componentes Reutilizáveis

| Componente | Classes CSS | Descrição |
|---|---|---|
| **Glass Panel** | `.glass-panel` | backdrop-filter: blur(12px), border sutil, bg semi-transparent |
| **Botão Primário** | Botão com bg primary, hover glow | CTA principal |
| **Botão WhatsApp** | Botão verde (#25D366) | CTA de contato |
| **Ícone Material** | `<span class="material-symbols-outlined">nome</span>` | Google Material Symbols |
| **Grid de Cards** | Grid 3 colunas (responsive) | Para listar serviços/soluções |
| **Carrossel** | Scroll horizontal com snap | Para depoimentos |

### Animações Padrão
- `@keyframes pulse` — glow pulsante em elementos de destaque
- `@keyframes glow` — brilho sutil em bordas
- `@keyframes scanning-line` — linha de scan animada (efeito tech)

## Procedimento

1. **Briefing**: Entenda o propósito da página (serviço, institucional, landing)
2. **Estrutura**: Crie o HTML semântico com `<header>`, `<main>`, `<section>`, `<footer>`
3. **Navbar**: Reutilize o padrão do header fixo com logo + navegação + CTA
4. **Seções**: Use o padrão de seções com padding adequado (`px-*` equivalente a 24px/64px)
5. **Glass Panels**: Use `.glass-panel` para cards e containers destacados
6. **Responsividade**: Aplique breakpoint mobile em 768px
7. **Ícones**: Use Material Symbols Outlined para ícones
8. **CTAs**: Inclua pelo menos um botão WhatsApp por página

## Arquivos de Referência
- `build/index.html` — página principal (padrão visual)
- `AGENTS.md` — convenções de código
- `docs/INSTITUCIONAL.md` — conteúdo institucional da empresa
