# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## O que é este projeto

Landing page estática para a masterclass **"O Código do Consultório Cirúrgico"** — evento ao vivo em 17 de maio (domingo, 08h–12h, Zoom), promovido pelo **Foco Cirúrgico**. Público-alvo: cirurgiões (não veterinários nem dentistas). Mentores: Marcelo Portocarrero, Lauro Matos, João Estrela, Eutímio Brasil. Ingressos R$ 297 (comum) e R$ 597 (VIP).

Sem build step. Tailwind via CDN, HTML puro. Pode ser hospedado em Netlify, Vercel ou GitHub Pages sem configuração adicional.

## Estrutura dos arquivos

```
index.html                 ← arquivo de produção (usar este)
code.html                  ← rascunho original do Stitch (referência)
DESIGN.md                  ← design system "Precision & Prestige"
screen.png                 ← mockup de referência do Stitch
Fotos-medicos/
  ├─ *.png                 ← originais (1–9 MB cada, masters)
  └─ web/                  ← versões otimizadas usadas no HTML
     ├─ marcelo.jpg  (foi IMG_7559.png)
     ├─ lauro.jpg
     ├─ joao.jpg
     └─ eutimio.jpg
logos/
  ├─ *.png                 ← originais
  └─ web/                  ← versões otimizadas
     ├─ logo-hero.png      ← "Colorida 02 Vertical Com Tagline" — header
     └─ logo-monograma.png ← "Negativo Monograma" — footer
```

`index.html` referencia exclusivamente os assets em `*/web/`. Os originais ficam como master para re-exportação se precisar.

## Decisões de design fixadas

- **Paleta**: fundo preto `#000000`, destaque dourado `#e5a81b`, texto principal `#ffffff`, auxiliar `#a3a3a3`. Definida no `tailwind.config` inline em [index.html](index.html).
- **Tipografia**: Josefin Sans (headlines/display) + Manrope (body). Importadas via Google Fonts com `preconnect`.
- **Mobile-first**: a experiência foi priorizada pensando em acesso por mobile. Tailwind já é mobile-first por padrão; classes sem breakpoint = mobile; `sm:`/`md:`/`lg:` aplicam em telas maiores.
- **Fotos dos médicos**: mantidas em grayscale (filtro `grayscale opacity-80`) para preservar a estética editorial do `DESIGN.md`.
- **Copyright**: "© 2026 Foco Cirúrgico. Todos os direitos reservados."

## Comandos úteis

### Abrir a página localmente
```bash
open "index.html"
```

### Re-otimizar imagens (se substituir originais)
```bash
# Fotos dos médicos: PNG → JPG 600px q82
sips -Z 600 -s format jpeg -s formatOptions 82 \
  "Fotos-medicos/NOME-original.png" --out "Fotos-medicos/web/nome.jpg"

# Logos: mantém PNG, só redimensiona
sips -Z 800 "logos/LOGO-original.png" --out "logos/web/logo-xxx.png"
```

Target: fotos ~60–80 KB cada, logos <50 KB. `sips` é built-in no macOS.

## Itens pendentes / para revisão futura

- **URL do CTA**: todos os botões "Quero participar..." apontam para `#inscricao` (scroll pra seção de preços). Trocar pela URL real de checkout quando disponível (Sympla, Hotmart, etc.).
- **Analytics**: não há GA, Meta Pixel nem tracking configurado.
- **Favicon**: usa o monograma (`logos/web/logo-monograma.png`) — considerar gerar um `.ico` otimizado se necessário.
- **Seções decorativas**: os 3 backgrounds de imagem do rascunho (`hero`, `target audience`, `pricing`) foram removidos por peso vs. benefício em mobile. Se quiser readicionar, usar imagens locais otimizadas <100 KB.

## Referência: copy original

A estrutura de seções e o texto completo estão em [code.html](code.html) (rascunho do Stitch). [index.html](index.html) é o derivado em produção. Para mudar copy, edite `index.html`; `code.html` fica como backup do rascunho.
