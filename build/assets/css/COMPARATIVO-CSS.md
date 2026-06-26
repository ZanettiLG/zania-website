# Comparativo CSS — Live Site (www.zan.ia.br) vs Local (build/index.html)

## 1. Abordagem Geral

| Aspecto | Live Site (www.zan.ia.br) | Local (build/) |
|---------|--------------------------|----------------|
| **Engine CSS** | Tailwind CDN (`cdn.tailwindcss.com` + plugins `forms,container-queries`) | CSS Vanilla (`tailwind-replacement.css` + módulos em `assets/css/`) |
| **Config** | `tailwind.config` inline no `<script>` | N/A — CSS escrito manualmente |
| **Custom CSS** | Inline `<style>` no `<head>` | Modular em `assets/css/components/*`, `assets/css/base/*`, `assets/css/utilities/*` |
| **Importação** | CDN + config inline + style inline | `main.css` com `@import` de módulos, `tailwind-replacement.css` no `<head>` |

---

## 2. Tailwind Config (live site)

```js
tailwind.config = {
    darkMode: "class",
    theme: {
        extend: {
            colors: {
                "surface-container-high": "#23293c",
                "on-primary": "#00363f",
                "on-tertiary-fixed-variant": "#3f465c",
                "tertiary-container": "#c4cce6",
                "inverse-primary": "#006877",
                "surface-container": "#191f31",
                "inverse-on-surface": "#2a3043",
                "on-error-container": "#ffdad6",
                "on-surface": "#dce1fb",
                "on-secondary-fixed-variant": "#39485a",
                "primary-container": "#00e0ff",
                "tertiary-fixed": "#dae2fd",
                "secondary-fixed-dim": "#b9c8de",
                "on-primary-fixed": "#001f25",
                "surface": "#0c1324",
                "surface-dim": "#0c1324",
                "surface-container-highest": "#2e3447",
                "secondary-container": "#39485a",
                "on-tertiary-container": "#4e566c",
                "primary": "#baf2ff",
                "on-secondary-container": "#a7b6cc",
                "tertiary": "#e2e8ff",
                "secondary-fixed": "#d4e4fa",
                "on-secondary-fixed": "#0d1c2d",
                "on-primary-container": "#005f6d",
                "secondary": "#b9c8de",
                "primary-fixed-dim": "#00daf8",
                "outline": "#859397",
                "primary-fixed": "#a5eeff",
                "inverse-surface": "#dce1fb",
                "surface-tint": "#00daf8",
                "tertiary-fixed-dim": "#bec6e0",
                "background": "#0c1324",
                "on-background": "#dce1fb",
                "outline-variant": "#3b494c",
                "on-secondary": "#233143",
                "on-error": "#690005"
            },
            borderRadius: {
                DEFAULT: "0.125rem",
                lg: "0.25rem",
                xl: "0.5rem",
                full: "0.75rem"
            },
            spacing: {
                gutter: "24px",
                "margin-mobile": "16px",
                "margin-desktop": "64px",
                base: "8px",
                "container-max": "1440px"
            },
            fontFamily: {
                "display-lg": ["Space Grotesk"],
                "headline-lg-mobile": ["Space Grotesk"],
                "headline-lg": ["Space Grotesk"],
                "code-md": ["JetBrains Mono"],
                "label-sm": ["JetBrains Mono"],
                "body-md": ["Geist"],
                "headline-md": ["Space Grotesk"],
                "body-lg": ["Geist"]
            },
            fontSize: {
                "display-lg": ["64px", { lineHeight: "1.1", letterSpacing: "-0.02em", fontWeight: "700" }],
                "headline-lg-mobile": ["32px", { lineHeight: "1.2", fontWeight: "600" }],
                "headline-lg": ["40px", { lineHeight: "1.2", fontWeight: "600" }],
                "code-md": ["14px", { lineHeight: "1.5", fontWeight: "400" }],
                "label-sm": ["12px", { lineHeight: "1.0", letterSpacing: "0.05em", fontWeight: "500" }],
                "body-md": ["16px", { lineHeight: "1.6", fontWeight: "400" }],
                "headline-md": ["24px", { lineHeight: "1.3", fontWeight: "500" }],
                "body-lg": ["18px", { lineHeight: "1.6", fontWeight: "400" }]
            }
        }
    }
}
```

---

## 3. CSS Custom Inline (live site)

```css
body {
    background-color: #070d1f;
    color: #dce1fb;
    overflow-x: hidden;
}

.glass-panel {
    background: rgba(15, 23, 42, 0.7);
    backdrop-filter: blur(12px);
    border: 1px solid rgba(186, 242, 255, 0.1);
}

.electric-glow {
    box-shadow: 0 0 15px rgba(0, 224, 255, 0.4);
}

.electric-glow-hover:hover {
    box-shadow: 0 0 25px rgba(0, 224, 255, 0.7);
}

.data-pulse { position: relative; }

.data-pulse::after {
    content: '';
    position: absolute;
    width: 4px;
    height: 4px;
    background: #00e0ff;
    border-radius: 50%;
    top: 50%;
    left: -10px;
    animation: pulse 2s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); opacity: 1; }
    100% { transform: scale(3); opacity: 0; }
}

.scanning-line {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, #00e0ff, transparent);
    position: absolute;
    top: 0;
    left: 0;
    animation: scan 3s linear infinite;
}

@keyframes scan {
    0% { top: 0; }
    100% { top: 100%; }
}

.material-symbols-outlined {
    font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 24;
}

.scrollbar-hide::-webkit-scrollbar { display: none; }
.scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
}
```

---

## 4. CSS do Local (build/assets/css/)

### 4.1 Design Tokens (`base/variables.css`)
Cores **idênticas** ao tailwind.config do live site. Mesmos valores para todas as variáveis `--color-*`, `--font-*`, `--spacing-*`.

### 4.2 Typography (`base/typography.css`)
Usa as variáveis CSS (`--font-display`, `--font-size-headline-lg`, etc.) que espelham o tailwind.config.

### 4.3 Reset (`base/reset.css`)
Reset básico + estilos base para `body`, `img`, `a`, `button`, `ul/ol`. O live site não tem reset explícito, usa o reset do Tailwind.

### 4.4 Componentes vs Live Site

| Componente | Local (modular) | Live Site (classes Tailwind) |
|---|---|---|
| **Header** | `.app-bar` + BEM | `fixed top-0 left-0 w-full z-50 bg-surface/80 backdrop-blur-xl border-b border-outline-variant/15 px-margin-mobile md:px-margin-desktop py-4 flex justify-between items-center max-w-container-max mx-auto` |
| **Hero** | `.hero__*` (BEM) | Classes Tailwind + estrutura similar |
| **Authority** | `.authority__*` (BEM) | Classes Tailwind + estrutura similar |
| **Solutions** | `.solutions__*` (BEM) | Classes Tailwind + estrutura similar |
| **Differential** | `.differential__*` (BEM) | Classes Tailwind + estrutura similar |
| **Testimonials** | `.testimonials__*` (BEM) | Classes Tailwind + estrutura similar |
| **CTA** | `.cta__*` (BEM) | Classes Tailwind + estrutura similar |
| **Footer** | `.footer__*` (BEM) | Classes Tailwind + estrutura similar |

### 4.5 Tailwind Replacement (`tailwind-replacement.css`)
Contém classes utilitárias que replicam as classes Tailwind usadas no HTML:
- Display, Flex, Grid, Spacing, Sizing, Typography, Colors, Borders, Effects
- **Diferença**: usa variáveis `--tw-*` em vez das `--color-*` dos tokens

---

## 5. Diferenças Críticas Encontradas

### 5.1 Border Radius Inconsistente

**Live site (Tailwind config):**
```
DEFAULT: 0.125rem (2px)
lg: 0.25rem (4px)
xl: 0.5rem (8px)
full: 0.75rem (12px)
```

**Local (tailwind-replacement.css):**
```css
.rounded { border-radius: 0.125rem; }
.rounded-sm { border-radius: 0.25rem; }
.rounded-md { border-radius: 0.375rem; }  /* ← DIFERENTE do Tailwind padrão */
.rounded-lg { border-radius: 0.5rem; }
.rounded-xl { border-radius: 0.75rem; }    /* ← DIFERENTE: live usa 0.5rem=8px */
.rounded-2xl { border-radius: 1rem; }
.rounded-3xl { border-radius: 1.5rem; }
.rounded-full { border-radius: 9999px; }
```

**Local (responsive.css):**
```css
.rounded-sm { border-radius: var(--radius-sm); }   /* 8px */
.rounded-md { border-radius: var(--radius-md); }    /* 12px */
.rounded-lg { border-radius: var(--radius-lg); }    /* 16px */
.rounded-xl { border-radius: var(--radius-xl); }    /* 24px */
.rounded-2xl { border-radius: calc(var(--radius-xl) * 1.33); } /* ~32px */
.rounded-3xl { border-radius: calc(var(--radius-xl) * 2); }    /* 48px */
.rounded-full { border-radius: var(--radius-full); } /* 9999px */
```

**⚠️ PROBLEMA:** `tailwind-replacement.css` e `responsive.css` definem valores DIFERENTES para as mesmas classes (`rounded-xl`, `rounded-2xl`, etc.). O `responsive.css` sobrescreve o `tailwind-replacement.css` porque é importado DEPOIS via `main.css`.

### 5.2 Box-shadow Inconsistente

**Live site (Tailwind):** usa as shadows padrão do Tailwind CDN.

**Local (tailwind-replacement.css):** usa shadows explícitas no formato Tailwind.
**Local (responsive.css):** usa `var(--shadow-lg)` e `var(--shadow-xl)`.

### 5.3 Glass Panel Duplicado

**Live site:** 1 definição inline.
**Local:** definido em `tailwind-replacement.css` (final) E em `utilities/glass-panel.css`. Mesmo código, mas duplicado.

### 5.4 Animações Duplicadas

**Live site:** 1 definição no style inline.
**Local:** `@keyframes pulse` e `@keyframes scan` definidos em `tailwind-replacement.css` E em `utilities/animations.css`.

### 5.5 Font Label SM

**Live site (Tailwind config):** `fontFamily["label-sm"]: ["JetBrains Mono"]`
**Local (typography.css):** `.font-label-sm { font-family: var(--font-body); ... }` — usa Geist em vez de JetBrains Mono!

**⚠️ PROBLEMA CRÍTICO:** O label-sm no local usa `var(--font-body)` (Geist), mas no live site deveria usar JetBrains Mono.

### 5.6 Background Surface Container

**Live site:** usa classes Tailwind como `bg-surface-container-lowest`.
**Local:** `.bg-surface-container-lowest` definido como `#070d1f` em `tailwind-replacement.css`. OK.

### 5.7 Header CTA Button

**Live site:** usa classes Tailwind como `bg-primary text-on-primary font-label-sm`.
**Local (header.css):** `.app-bar__cta` com `font-family: var(--font-body)` (Geist) — mesmo problema do label-sm.

---

## 6. Resumo das Correções Necessárias

1. **`typography.css`**: `.font-label-sm` deve usar `var(--font-code)` (JetBrains Mono) em vez de `var(--font-body)` (Geist)
2. **`tailwind-replacement.css`**: valores de `rounded-*` conflitam com `responsive.css` — unificar
3. **`tailwind-replacement.css`**: `.rounded-xl` deve ser `0.5rem` (8px) não `0.75rem` (12px) para igualar Tailwind config do live
4. **Duplicação**: `glass-panel`, `scanning-line`, `data-pulse`, `@keyframes` repetidos em múltiplos arquivos
5. **`header.css`**: `.app-bar__cta` deve usar `font-family: var(--font-code)` (JetBrains Mono)
