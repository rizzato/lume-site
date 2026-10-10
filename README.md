# LUMË — Site da Clínica Geriátrica

Landing page única da clínica **LUMË**, da Dra. Julia Lassance (Geriatria & Clínica Geral).

Site estático (HTML + CSS + JS puros), sem dependências ou build. Basta abrir o `index.html` no navegador ou publicar em qualquer hospedagem.

## Arquivos

```
lume-site/
├── index.html               # Página principal (todas as seções)
├── 404.html                 # Página de erro no padrão da marca
├── robots.txt               # Indexação BLOQUEADA (beta) — ver DEPLOY.md
├── sitemap.xml              # Mapa do site (SEO)
├── DEPLOY.md                # Guia de publicação no GitHub Pages
├── .nojekyll                # Desativa o Jekyll no GitHub Pages
├── .gitignore               # Mantém assets/fotos/ fora do repositório
├── css/
│   └── styles.css           # Cores, fontes e layout
├── js/
│   └── script.js            # Menu mobile, header e animações
└── assets/
    ├── favicon.svg          # Ícone Ë (aba do navegador)
    ├── apple-touch-icon.png # Ícone iOS (180×180)
    ├── og-image.jpg         # Preview ao compartilhar (1200×630)
    └── img/                 # Fotos otimizadas em WebP
```

## Identidade visual (Manual de Marca · ago/2026)

| Item | Valor |
|------|-------|
| Cor primária | `#A39D96` |
| Cor secundária | `#B8B298` (champagne) |
| Texto | `#58534B` |
| Texto secundário | `#6B655D` (contraste AA) |
| Fundo creme | `#E0CFBF` |
| Fonte principal | Afacad Flux |
| Fonte secundária | Poppins |

O logotipo (**"CLÍNICA" sobre "LUMË"**) está embutido como SVG vetorial, com a cor controlada por CSS (`currentColor`).

> **Importante:** o `viewBox` do SVG foi recortado para remover o espaço vazio interno do arquivo original. Sem esse recorte, o logo ocupava apenas ~61% da altura definida e parecia menor do que realmente era.

## Acessibilidade (público 60+)

- Texto base **17px** e corpo dos cards **16px** (presbiopia).
- Todos os textos atendem **WCAG AA** (≥ 4,5:1) — verificado cor a cor.
- Foco de teclado visível (`:focus-visible`).
- `prefers-reduced-motion` respeitado, skip-link e `alt` em todas as imagens.

## Como visualizar localmente

```bash
cd C:\Users\Rafael\julia\lume-site
python -m http.server 8080
```

Depois abra `http://localhost:8080`.

## Antes de publicar — pendências

**Bloqueadores**

- [ ] **Telefone**: `+55 11 91234-5678` é **placeholder fictício**. Trocar pelo número real da clínica — aparece em 5 pontos da página **e também no JSON-LD** dentro do `<head>`.
- [ ] **`robots.txt`**: está com `Disallow: /` bloqueando o Google (intencional no beta). Trocar para `Allow: /` no lançamento.
- [ ] **Consentimento de imagem (LGPD)**: as fotos `acolhimento.webp` e `mobilidade.webp` mostram pacientes identificáveis — publicar somente com autorização.
- [ ] **Mapa**: conferir em navegador real se o embed carrega (no Chrome headless ele aparece vazio). Existe o link **"Abrir no Google Maps"** como fallback. Se não carregar, trocar pelo embed oficial (`/maps/embed?pb=…`, gerado em "Compartilhar → Incorporar mapa").

**Conteúdo**

- [ ] **Horário de atendimento**: ainda não incluído no site.
- [ ] **Serviços**: 12 cards (6 padrão + 6 indicados pela Dra. Julia) — revisar descrições.
- [ ] **Biografia/credenciais**: baseada no currículo Lattes + informações da Dra. Julia — revisar (CRM/RQE, SBGG, ILPI).
- [ ] **Retrato**: o jaleco traz "Santa Cruz" bordado — avaliar se quer trocar a foto.

**Observações**

- O `og:image` aponta para `https://lume.med/...` (domínio de produção). Enquanto o HTTPS do domínio não estiver ativo, o preview ao compartilhar pode não exibir a imagem.
- O botão flutuante do WhatsApp usa o verde oficial (`#25D366`) — desvio consciente da paleta, por reconhecimento.
- `assets/fotos/` (originais em alta resolução) fica fora do repositório — ver `.gitignore`.

## Dados de contato usados

- E-mail: `clinica@lume.med`
- Site: `www.lume.med`
- CRM 142225 · RQE 62172
