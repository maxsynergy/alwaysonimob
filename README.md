# AlwaysOn Imob — Landing Page de Captura de Leads

Landing page estática de alta conversão para venda do serviço **Atendimento Always-On (24/7)** voltado a imobiliárias de médio padrão.

Desenvolvida por MaxSyn Assessoria com HTML, CSS e JavaScript puros — **zero dependências, zero build step**. Deploy instantâneo na Vercel ou Netlify.

---

## 🚀 Deploy em 1 clique

### Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)

1. Faça fork deste repositório
2. Acesse [vercel.com](https://vercel.com) → **Add New Project**
3. Importe o repositório
4. Clique em **Deploy** — sem configuração adicional

### Netlify

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start)

1. Acesse [netlify.com](https://netlify.com) → **Add new site** → **Import an existing project**
2. Conecte ao GitHub e selecione o repositório
3. Deixe **Build command** e **Publish directory** em branco
4. Clique em **Deploy site**

---

## 📁 Estrutura do repositório

```
/
└── atendimento-always-on-imobiliarias.html   # Página principal (único arquivo necessário)
└── README.md
└── img
└──── alwayonimob-24-7.png
└──── alwayonimob-funciona.png
```

> **Importante:** para que a Vercel e o Netlify sirvam o arquivo como página raiz, renomeie-o para `index.html` antes de subir.

```bash
mv atendimento-always-on-imobiliarias.html index.html
```

---

## ✏️ Personalizações essenciais antes de publicar

Abra o arquivo `index.html` e ajuste os seguintes pontos:

### 1. Identidade da marca

| Onde | O que trocar |
|---|---|
| `<title>` e meta tags | Nome da sua empresa/serviço |
| `.nav-logo` (linha ~320) | Substitua `AlwaysOn Imob` pela sua marca |
| `footer` | Razão social e ano |

### 2. Formulário de captura — integração com backend

O botão de envio chama a função `handleSubmit()`. Conecte ao seu serviço de preferência descomentando e adaptando a linha indicada no script:

```js
// Exemplo com fetch para seu endpoint ou webhook
fetch('/api/leads', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ nome, whatsapp, imobiliaria, cidade, corretores })
});
```

**Serviços recomendados (sem backend próprio):**

| Serviço | Como usar |
|---|---|
| [Formspree](https://formspree.io) | Adicione `action="https://formspree.io/f/SEU_ID"` no form |
| [Make (Integromat)](https://make.com) | Webhook → Google Sheets / CRM / WhatsApp |
| [n8n](https://n8n.io) | Webhook self-hosted → qualquer destino |
| [Zapier](https://zapier.com) | Webhook → HubSpot, Pipedrive, planilha |

### 3. SEO — campos obrigatórios

Antes de publicar, edite o bloco `<head>`:

```html
<!-- Troque pela URL real do seu domínio -->
<link rel="canonical" href="https://seudominio.com.br/atendimento-always-on-imobiliarias" />

<!-- Open Graph — aparece ao compartilhar no WhatsApp/LinkedIn -->
<meta property="og:url" content="https://seudominio.com.br/..." />
<meta property="og:image" content="https://seudominio.com.br/og-image.jpg" />
```

> Adicione uma imagem `og:image` de **1200×630px** para preview rico ao compartilhar.

### 4. Google Analytics / Meta Pixel

Cole seus snippets imediatamente antes de `</head>`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>

<!-- Meta Pixel -->
<script>
  !function(f,b,e,v,n,t,s){...}(window,document,'script',
  'https://connect.facebook.net/en_US/fbevents.js');
  fbq('init', 'SEU_PIXEL_ID');
  fbq('track', 'PageView');
</script>
```

### 5. Domínio customizado

- **Vercel:** Configurações do projeto → **Domains** → adicione seu domínio
- **Netlify:** Site settings → **Domain management** → **Add custom domain**

---

## 🔍 Checklist de SEO pré-publicação

- [ ] `<title>` com palavra-chave principal
- [ ] `meta description` entre 140–160 caracteres
- [ ] URL canônica apontando para o domínio real
- [ ] Imagem `og:image` criada e hospedada (1200×630px)
- [ ] Google Analytics ou GTM instalado
- [ ] Google Search Console: domínio verificado e sitemap enviado
- [ ] Teste no [PageSpeed Insights](https://pagespeed.web.dev/)
- [ ] Teste no [Schema Markup Validator](https://validator.schema.org/)
- [ ] Formulário testado com envio real

---

## 🛠️ Desenvolvimento local

Não há build. Basta abrir o arquivo no navegador:

```bash
# Opção 1 — abrir direto
open index.html

# Opção 2 — servidor local simples com Python
python3 -m http.server 3000
# acesse: http://localhost:3000

# Opção 3 — com Node.js (npx)
npx serve .
# acesse: http://localhost:3000
```

---

## 📄 Licença

Uso privado. Todos os direitos reservados.