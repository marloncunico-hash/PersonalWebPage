# marloncunico.com

Site pessoal de **Marlon Cunico** — executivo de P&D e indústria.
HTML estático, sem framework e sem build: o que está no repositório é o que vai para o ar.

- `/` — versão em português
- `/en/` — versão em inglês
- Hospedagem prevista: **GitHub Pages** com domínio próprio `www.marloncunico.com`

---

## Estrutura

```
.
├── index.html              página em português
├── en/index.html           página em inglês
├── 404.html                página de erro
├── CNAME                   domínio do GitHub Pages (www.marloncunico.com)
├── .nojekyll               desliga o Jekyll (evita que pastas com _ sejam ignoradas)
├── robots.txt
├── sitemap.xml
├── assets/
│   ├── css/style.css       toda a folha de estilo (as duas páginas usam a mesma)
│   ├── js/main.js          menu móvel e destaque da seção atual
│   └── img/
│       ├── favicon.svg     ícone da aba
│       ├── og-image.png    imagem de compartilhamento (1200×630)
│       └── foto-marlon.jpg  <-- VOCÊ COLOCA (opcional, proporção 4:5)
└── cv/
    ├── cv-marlon-cunico.pdf     <-- VOCÊ COLOCA (currículo PT)
    └── cv-marlon-cunico-en.pdf  <-- VOCÊ COLOCA (currículo EN)
```

---

## Antes de publicar — 4 substituições

| O quê | Onde | Como está hoje |
|---|---|---|
| **WhatsApp** | `index.html` e `en/index.html`, seção de contato | `https://wa.me/5541999999999` — troque pelo número real: 55 + DDD + número, sem espaços nem traços |
| **LinkedIn** | mesmas duas linhas | `https://www.linkedin.com/in/marloncunico/` — confirme se é essa mesmo a URL do seu perfil |
| **PDFs do currículo** | pasta `cv/` | os botões apontam para `cv/cv-marlon-cunico.pdf` e `cv/cv-marlon-cunico-en.pdf`; enquanto não existirem, o clique cai no 404 |
| **Foto** | `assets/img/foto-marlon.jpg` | basta colocar o arquivo com esse nome, na proporção 4:5 (ex.: 880×1100 px). Sem o arquivo, aparece o monograma "MC" — o site não quebra |

Cada ponto está marcado com um comentário `<!-- TROQUE ... -->` no HTML.

---

## Publicar no GitHub Pages

### 1. Criar o repositório

No GitHub, **New repository** → nome `marloncunico.com` (ou o que preferir), **público**.
Suba os arquivos: pelo site (Add file → Upload files, arraste tudo, inclusive as pastas) ou pelo terminal:

```bash
git init
git add .
git commit -m "Site pessoal"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/marloncunico.com.git
git push -u origin main
```

> Se subir pelo navegador, confira depois se o arquivo `.nojekyll` foi junto — arquivos que começam com ponto às vezes ficam ocultos no seletor do sistema.

### 2. Ligar o Pages

**Settings → Pages**
- *Source*: `Deploy from a branch`
- *Branch*: `main` · pasta `/ (root)` → **Save**

Em um ou dois minutos o site sai em `https://SEU-USUARIO.github.io/marloncunico.com/`.

### 3. Apontar o domínio

**Settings → Pages → Custom domain**: digite `www.marloncunico.com` e salve.
(O arquivo `CNAME` já vem com esse valor; se você preferir usar o domínio sem `www`, veja a observação abaixo.)

No painel de DNS do seu registrador, crie:

| Tipo | Nome | Valor |
|---|---|---|
| CNAME | `www` | `SEU-USUARIO.github.io` |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

Os quatro registros A fazem o domínio sem `www` redirecionar para o `www`.
Depois que o DNS propagar (de minutos a algumas horas), volte em **Settings → Pages** e marque **Enforce HTTPS**.

> **Se preferir o domínio sem www** (`marloncunico.com`): troque o conteúdo do arquivo `CNAME` para `marloncunico.com`, use o mesmo valor no campo *Custom domain* e, nos dois `index.html` mais no `sitemap.xml` e no `robots.txt`, substitua `https://www.marloncunico.com` por `https://marloncunico.com`. São os campos `canonical`, `hreflang`, `og:url` e `og:image`.

### 4. Google Sites

Depois que o novo site estiver no ar no domínio, desligue a publicação do Google Sites ou deixe uma página única apontando para cá — dois sites no ar com o mesmo conteúdo dividem o resultado da busca pelo seu nome.

### 5. Avisar o Google

Em [Google Search Console](https://search.google.com/search-console), adicione a propriedade `www.marloncunico.com`, valide pelo DNS e envie `https://www.marloncunico.com/sitemap.xml`. É o que acelera a atualização do que aparece quando alguém busca o seu nome.

---

## Como editar depois

- **Texto**: os dois `index.html` são HTML puro e comentado por seção (`<!-- ==== RESULTADOS ==== -->`). Mudou algo em português, mude o equivalente em `/en/`.
- **Cores e espaçamentos**: as variáveis no topo de `assets/css/style.css` (`--navy`, `--teal`, `--surface`…). Trocar `--teal` muda o acento do site inteiro.
- **Uma seção nova**: copie um `<section class="section">` inteiro, troque o `id` e acrescente o link correspondente no `<nav>`.
- **Ordem das seções**: recortar e colar o bloco `<section>` inteiro. Nada depende da ordem.

O site funciona sem JavaScript (o menu móvel e o destaque do menu são o único uso) e imprime em PDF limpo — `Ctrl/Cmd + P` gera uma versão sem menu e sem fundos escuros.

---

## Verificações rápidas depois de publicar

1. Abra no celular — o menu vira botão, as colunas empilham.
2. Cole `https://www.marloncunico.com` no LinkedIn ou no WhatsApp e veja se a imagem de compartilhamento aparece.
3. Clique nos quatro botões de contato e no download do currículo.
4. Teste o `/en/` e o botão PT/EN nos dois sentidos.
5. Rode o [Rich Results Test](https://search.google.com/test/rich-results) na home — os dados estruturados `Person` devem ser reconhecidos.
