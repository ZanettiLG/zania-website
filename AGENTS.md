# Zan.IA Website — Agent Guidelines

## Project Overview

Landing page institucional para **Zan.IA** — empresa de tecnologia focada em desenvolvimento web, agentes de IA, automação e criação de mídia assistida por inteligência artificial.

> Consulte [`docs/INSTITUCIONAL.md`](./docs/INSTITUCIONAL.md) para visão completa da empresa, serviços e diferenciais.

## Tech Stack

| Camada | Tecnologia |
|--------|-----------|
| **Markup** | HTML5 semântico (monolítico) |
| **Estilos** | Tailwind CSS 3 via CDN + CSS vanilla inline |
| **Ícones** | Google Material Symbols Outlined |
| **Tipografia** | Space Grotesk, Geist, JetBrains Mono (Google Fonts) |
| **Tema** | Dark mode (Material Design 3) |
| **Deploy** | GitHub Pages + GitHub Actions |

## Architecture

- **Único arquivo:** `build/index.html` contém todo HTML, CSS e JS
- **Sem build step:** Projeto estático puro, sem bundler ou framework
- **Sem dependências npm:** Tudo carregado via CDN

## Build & Deploy

```bash
# Não há build — o HTML está pronto em build/index.html
# Deploy automático via GitHub Actions ao push na branch main
# workflow: .github/workflows/static.yml
# Servido de: ./build/
```

## Estrutura de Arquivos

```
zania-website/
├── build/
│   └── index.html          # Landing page completa (produção)
├── docs/
│   └── INSTITUCIONAL.md    # Documento institucional da empresa
├── .github/
│   ├── ISSUES.md           # Plano de refatoração (3 issues prioritárias)
│   └── workflows/
│       └── static.yml      # Deploy GitHub Pages
└── AGENTS.md               # Este arquivo
```

## Convenções de Código

- **Classes Tailwind:** Usar classes utilitárias do Tailwind (`flex`, `items-center`, `gap-*`, `px-*`)
- **Design Tokens:** Usar variáveis CSS `--color-*`, `--font-*`, `--spacing-*` definidas em `:root`
- **Animações:** Preferir CSS `@keyframes` para efeitos (pulse, glow, scanning-line)
- **Ícones:** Usar `<span class="material-symbols-outlined">icon_name</span>`
- **Responsividade:** Breakpoint mobile em 768px via media queries
- **Glass panels:** Classe `.glass-panel` com backdrop-filter e borda sutil

## GitHub Workflow (Issues & PRs)

### Auto-close de Issues
- Incluir `Closes #N` (ou `Fixes`/`Resolves`) no corpo do PR — GitHub fecha a issue automaticamente ao mergear.
- **Verificar** se a issue foi fechada após o merge. Se não, fechar manualmente com `state=closed`, `reason=completed`.

### Fluxo Recomendado
1. Criar branch a partir de `main` (`feat/nome-descritivo`)
2. Fazer commit com mensagem descritiva (imperativo, < 72 chars)
3. Incluir `Closes #N` no corpo do PR
4. Abrir PR apontando para `main`
5. Após merge, confirmar que a issue foi fechada

## Refatoração Planejada

Veja [`.github/ISSUES.md`](./.github/ISSUES.md) para o plano completo de refatoração:

1. **Migrar Tailwind CDN → CSS vanilla** com estrutura modular (`css/base/`, `css/components/`, `css/utilities/`)
2. **Modularizar HTML** em componentes semânticos
3. **Localizar imagens** (remover dependência de CDNs externas)

## Canais de Contato

- WhatsApp (CTA principal): link direto para número da empresa
- Footer: links institucionais
