# 🚀 Publicar o site LUMË no GitHub Pages

Guia passo a passo para colocar o site no ar gratuitamente.

---

## ⚠️ Antes de começar — 2 avisos importantes

**1) O repositório precisa ser PÚBLICO.**
No plano gratuito do GitHub, o GitHub Pages **só funciona em repositórios públicos** (repositório privado exigiria GitHub Pro, que é pago). Como o site é público de qualquer forma, não há problema — mas saiba que **todo o conteúdo do repositório fica visível**, incluindo o código-fonte.

**2) A pasta `assets/fotos/` ficou FORA do repositório.**
Ela guarda as fotos originais em alta resolução e as descrições. Foi excluída de propósito via `.gitignore`, porque:
- o site não a usa (ele usa só `assets/img/*.webp`, já otimizadas);
- evita publicar as fotos de pacientes em resolução máxima.

Ela **continua no seu disco** como backup.

---

## 1. Criar o repositório no GitHub

1. Acesse **https://github.com/new**
2. **Repository name:** `lume-site`
3. **Visibility:** `Public` ⚠️ (obrigatório para Pages no plano gratuito)
4. **NÃO** marque "Add a README file" (o projeto já tem arquivos)
5. Clique em **Create repository**

---

## 2. Enviar o site para o GitHub

O repositório local **já está pronto**, com o commit inicial feito e o `remote` já apontando para `https://github.com/rizzato/lume-site.git`.

Depois de criar o repositório no GitHub (passo 1), basta rodar no **PowerShell**:

```powershell
cd C:\Users\Rafael\julia\lume-site
git push -u origin main
```

> **Login:** na primeira vez o Git vai pedir autenticação. Se pedir **senha**, não use a senha da conta — gere um **Personal Access Token**:
> GitHub → *Settings* → *Developer settings* → *Personal access tokens* → **Tokens (classic)** → *Generate new token* → marque o escopo **`repo`** → copie e use como senha.

---

## 3. Ativar o GitHub Pages

1. No repositório, vá em **Settings** → **Pages** (menu lateral esquerdo)
2. Em **Source**, selecione: **Deploy from a branch**
3. **Branch:** `main` — pasta **`/ (root)`**
4. Clique em **Save**
5. Aguarde ~1 minuto

✅ O site já estará no ar em:

```
https://rizzato.github.io/lume-site/
```

---

## 4. Domínio próprio (`lume.med`)

### 4.1 Informar o domínio no GitHub

Em **Settings → Pages → Custom domain**, digite `lume.med` e clique em **Save**.
O GitHub cria sozinho um arquivo `CNAME` no repositório.

### 4.2 Configurar o DNS

No painel onde o DNS do `lume.med` é gerenciado, crie/ajuste:

**Domínio raiz (`lume.med`)** — 4 registros `A`:

| Tipo | Nome | Valor |
|------|------|-------|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

**Subdomínio `www`** — 1 registro `CNAME`:

| Tipo | Nome | Valor |
|------|------|-------|
| CNAME | `www` | `rizzato.github.io` |

> 🔴 **NÃO MEXA nos registros `MX`.** São eles que fazem o e-mail `clinica@lume.med` do Google Workspace funcionar. Altere **apenas** registros `A` e `CNAME`.
>
> ⚠️ Se já existir um registro `A` no `@` apontando para outro serviço, ele deve ser **substituído** pelos 4 acima.
>
> ℹ️ Confirme os IPs atuais em: https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site

### 4.3 Ativar HTTPS

Volte em **Settings → Pages**, aguarde a verificação do DNS (de minutos a algumas horas) e marque **Enforce HTTPS**. O certificado é gratuito (Let's Encrypt) e se renova sozinho.

---

## 5. Atualizar o site depois

Sempre que alterar algum arquivo:

```powershell
cd C:\Users\Rafael\julia\lume-site
git add .
git commit -m "descrição da alteração"
git push
```

O GitHub Pages republica automaticamente em cerca de 1 minuto.

---

## 6. ⚠️ Checklist ANTES de tornar o site oficial

- [ ] **`robots.txt`** — hoje está com `Disallow: /`, que **bloqueia o Google durante o beta**. Para liberar a indexação, troque por `Allow: /` (as instruções estão dentro do próprio arquivo).
- [ ] **Telefone** — trocar o placeholder `+55 11 91234-5678` pelo número real da clínica (`index.html` e `README.md`).
- [ ] **Consentimento de imagem (LGPD)** — confirmar autorização dos pacientes nas fotos `acolhimento.webp` e `mobilidade.webp`.
- [ ] **Descrições dos serviços** — revisar com a Dra. Julia.
- [ ] **Mapa** — conferir se o pino cai no endereço correto.
- [ ] **CRM 142225 · RQE 62172** — confirmar os números.

---

## Estrutura publicada

```
lume-site/              ← raiz do repositório
├── index.html
├── 404.html
├── robots.txt
├── CNAME               (criado pelo GitHub ao configurar o domínio)
├── .nojekyll           (desativa o Jekyll — necessário para site estático puro)
├── .gitignore
├── README.md
├── DEPLOY.md
├── css/
│   └── styles.css
├── js/
│   └── script.js
└── assets/
    ├── favicon.svg
    └── img/            (4 imagens .webp otimizadas)
```

> `assets/fotos/` **não** vai para o repositório — ver aviso 2 no topo.
