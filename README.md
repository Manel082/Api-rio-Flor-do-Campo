# 🍯 Apiário Flor do Campo — Landing Page

Landing page do **Apiário Flor do Campo**, produtor de mel de abelha 100% natural em **Capela – Alagoas**.
O objetivo da página é apresentar o produto e levar o visitante a fazer o pedido pelo **WhatsApp**.

🔗 **Produção:** https://api-rio-flor-do-campo.vercel.app

---

## ✨ Visão geral

- **Site estático em um único arquivo** (`index.html`): HTML, CSS e JavaScript inline, sem build e sem dependências.
- A **logo** e a **foto do produto** estão embutidas no próprio HTML (base64). Não existe pasta de imagens para subir junto.
- Todos os botões abrem o **WhatsApp com uma mensagem pronta**, diferente para cada ponto da página.
- Layout **responsivo**: no celular o menu vira hambúrguer e a arte do topo aparece antes do texto.

## 🧱 Seções da página

| Seção | Âncora | Conteúdo |
|---|---|---|
| Preloader | — | Tela de carregamento com cascata de mel e abelha (mínimo de 3s, liberação garantida em 5s) |
| Header | `#topo` | Logo, menu e botão "Pedir pelo WhatsApp" |
| Hero | `#inicio` | Chamada principal, selos (responsável técnico, entrega etc.) e pote ilustrado com abelha interativa |
| O verdadeiro sabor | `#sabor` | Diferenciais do mel em lista |
| Da colmeia até você | — | Processo em 4 etapas |
| Sobre | `#sobre` | História do apiário |
| Nosso mel | `#nosso-mel` | Card do produto com foto real, ficha técnica e botão de pedido |
| Qualidade | `#qualidade` | 4 pilares de qualidade |
| Depoimentos | `#depoimentos` | **Comentada**, aguardando depoimentos reais |
| CTA final | `#contato` | Chamada final para o WhatsApp |
| Rodapé | — | Contato, localização e copyright (ano automático) |

## 🎛️ Interações

- Header ganha sombra ao rolar a página.
- Elementos aparecem com animação ao entrar na tela (`IntersectionObserver`).
- Abelha do topo **pousa na flor ao ser clicada** (também funciona com Enter/Espaço).
- **Cursor de mel** personalizado, só em dispositivos com mouse.
- **Efeito 3D (tilt)** no card do produto.
- Botão flutuante de WhatsApp com animação de pulso.
- Respeita `prefers-reduced-motion`: animações são desativadas para quem pediu menos movimento no sistema.

---

## ✏️ Como editar

### Número do WhatsApp
No `<script>` ao final do arquivo:

```js
const WHATS_NUMERO = '5582999500457';      // DDI + DDD + número, só dígitos
const WHATS_EXIBICAO = '(82) 99950-0457';  // como aparece no rodapé
```

### Mensagens prontas
Cada botão tem um atributo `data-msg` com o texto que já chega digitado no WhatsApp:

```html
<a href="#" class="btn btn-verde js-whats" data-msg="Olá! Gostaria de saber o valor...">
```

Qualquer link com a classe `js-whats` vira automaticamente um link de WhatsApp.

### Cores e fontes
Ficam centralizadas nas variáveis do `:root`, no início do CSS:

```css
--mel: #F2A516;      /* dourado principal */
--marrom: #3B2412;   /* títulos */
--verde: #25A244;    /* botões de pedido */
--serif: 'Lora';     /* títulos */
--sans: 'Poppins';   /* textos */
```

As fontes vêm do Google Fonts. É o único recurso externo da página.

### Trocar ou adicionar fotos
As áreas ainda ilustradas (hero, "O verdadeiro sabor" e "Sobre") têm um comentário logo acima explicando como trocar o desenho por uma `<img>`.

Há duas formas de usar uma foto:

1. **Arquivo separado (recomendado para fotos novas):** coloque a imagem na raiz do projeto (ex.: `foto-apicultor.webp`) e use `<img src="foto-apicultor.webp" alt="...">`.
2. **Embutida em base64:** é como estão a logo e a foto do produto. O arquivo fica autossuficiente, mas mais pesado.

> 💡 Antes de subir uma foto, converta para **WebP** e reduza para ~1100px de largura. Isso costuma deixar a imagem abaixo de 100 KB.

### Ativar os depoimentos
1. Procure o bloco `DEPOIMENTOS (opcional)` no HTML e remova os marcadores de comentário `<!--` e `-->`.
2. Preencha com **depoimentos reais** de clientes.
3. Adicione o item no menu: `<li><a href="#depoimentos">Depoimentos</a></li>`.

### Instagram
No rodapé há uma linha comentada pronta. Basta descomentar e trocar `SEU_PERFIL`.

### Tempo do preloader
```js
const TEMPO_MINIMO_PRELOADER = 3000; // em milissegundos
```

---

## 🚀 Deploy (Vercel)

O projeto não tem build. A Vercel só precisa encontrar o `index.html` **na raiz**.

**Configuração do projeto** (*Settings → Build and Deployment*):

| Campo | Valor |
|---|---|
| Framework Preset | `Other` |
| Build Command | vazio |
| Output Directory | vazio |
| Install Command | vazio |
| Root Directory | pasta onde está o `index.html` |

**Via GitHub:** faça push com o `index.html` na raiz do repositório. Cada push faz um novo deploy automaticamente.

**Via CLI:**
```bash
npx vercel --prod
```

> ⚠️ **Erro `404: NOT_FOUND`?** A Vercel não encontrou o `index.html` na raiz. Confira se o arquivo não está numa subpasta, se o nome não ficou `index (1).html` e se o Framework Preset não está como Vite/React.

## 💻 Rodando localmente

Abra o `index.html` direto no navegador, ou sirva a pasta:

```bash
npx serve .
```

---

## 📁 Estrutura

```
.
├── index.html   # página completa (HTML + CSS + JS + imagens embutidas)
└── README.md
```

## 📇 Informações do negócio

- **Empresa:** Apiário Flor do Campo
- **Produto:** Mel de abelha 100% natural, embalagem de 700g
- **Origem:** Capela – AL
- **Responsável técnico:** Luciano Fragoso
- **Vendas:** pelo WhatsApp, com entrega em domicílio

---

Desenvolvido por **Emmanuel** · Maceió – AL
