# LUMË — Site da Clínica Geriátrica

Landing page única da clínica **LUMË**, da Dra. Julia Lassance (Geriatria & Clínica Geral).

Site estático (HTML + CSS + JS puros), sem dependências ou build. Basta abrir o `index.html` no navegador ou publicar em qualquer hospedagem (Vercel, Netlify, GitHub Pages, cPanel, etc.).

## Arquivos

```
lume-site/
├── index.html          # Página principal (todas as seções)
├── css/
│   └── styles.css      # Cores e fontes conforme o Manual de Marca
├── js/
│   └── script.js       # Menu mobile, header e animações de revelação
└── assets/
    └── favicon.svg     # Ícone Ë da marca
```

## Identidade visual aplicada (Manual de Marca · ago/2026)

| Item | Valor |
|------|-------|
| Cor primária | `#A39D96` |
| Cor secundária | `#B8B298` (champagne) |
| Texto | `#58534B` |
| Fundo creme | `#E0CFBF` |
| Fonte principal | Afacad Flux |
| Fonte secundária | Poppins |

O logotipo **LUMË** (LUM + ícone Ë) está embutido como SVG vetorial, com a cor controlada por CSS (`currentColor`) — nada de imagens borradas.

## Como visualizar localmente

1. Dê um duplo clique em `index.html`, **ou** sirva por um servidor local para simular produção:

```bash
# Python (já instalado no seu Windows)
python -m http.server 8080
```

2. Abra `http://localhost:8080` no navegador.

## Antes de publicar — revisar

- [ ] **Serviços** (seção "Serviços"): 12 cards (6 padrão + 6 indicados pela Dra. Julia). Revisar descrições e ordem antes de publicar.
- [ ] **Biografia/credenciais da Dra. Julia**: preenchidas com base no currículo Lattes e nas informações da Dra. Julia — revisar antes de publicar (CRM/RQE, SBGG, ILPI).
- [ ] **Endereço**: configurado como *Av. Portugal, 1629 · cj. 12 · Brooklin · São Paulo/SP* (conforme escolha).
- [ ] **WhatsApp/telefone**: `+55 11 91234-5678` — **PLACEHOLDER fictício**. Substituir pelo número real da clínica antes da publicação definitiva (aparece no botão do topo, no card de contato, no CTA final, no rodapé e no botão flutuante).
- [ ] **Instagram**: https://www.instagram.com/julialassance/ (LinkedIn omitido).
- [ ] **Mapa**: embutido via Google Maps com a consulta do endereço — conferir se o pino cai no local certo.
- [ ] **Consentimento de imagem**: as fotos `acolhimento.webp` e `mobilidade.webp` mostram pacientes — usar apenas com autorização (LGPD).
- [ ] **Foto `IMG_0980.jpg`**: removida da galeria por possível marca de geração/edição por IA — reavaliar antes de usar.
- [ ] Horários de atendimento (não incluídos — adicionar se desejar).

## Dados de contato usados

- E-mail: `clinica@lume.med`
- Site: `www.lume.med`
- CRM 142225 · RQE 62172
