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
└── assets/
    ├── css/style.css        toda a folha de estilo (as duas páginas usam a mesma)
    ├── js/main.js           menu móvel e destaque da seção atual
    └── img/
        ├── favicon.svg      ícone da aba
        ├── og-image.png     imagem de compartilhamento (1200×630, com a foto)
        └── marlon-cunico.jpg  foto do hero (4:5)
```

---

## O que já está preenchido

| Item | Valor no site |
|---|---|
| Foto | `assets/img/marlon-cunico.jpg` — recorte 4:5 da foto do projeto. Para trocar, substitua o arquivo mantendo o nome e a proporção |
| Telefone e WhatsApp | +55 41 99670-4747 — visível na seção de contato, com botão de ligar (`tel:`) e de WhatsApp (`wa.me`) |
| E-mail | marloncunico@gmail.com |
| LinkedIn | `linkedin.com/in/marlon-cunico-b2b38110` — endereço confirmado na auditoria de agosto |
| Currículo PT | Google Docs — *CV_Executivo_Marlon_Cunico_PT*, aberto em modo leitura (`/preview`) |
| Currículo EN | Google Docs — *CV_Executive_Marlon_Cunico_EN*, aberto em modo leitura (`/preview`) |

### Duas verificações antes de divulgar

1. **Permissão dos documentos.** Abra os dois links do currículo numa janela anônima. Se aparecer "Você precisa de acesso", o headhunter verá o mesmo — no Drive, mude o compartilhamento para *Qualquer pessoa com o link · Leitor*.
2. **Versão detalhada.** Os CVs detalhados (4 páginas, PT e EN) ficaram de fora por decisão de projeto: o site oferece só a versão executiva. Se quiser incluí-los depois, é um `<a class="btn btn--ghost">` a mais na seção de contato.

> **Se preferir PDF hospedado aqui em vez do Google Docs:** crie uma pasta `cv/`, coloque os arquivos e troque as URLs do Google nos dois `index.html` (são quatro ocorrências, duas por página: hero e contato). PDF carrega mais rápido, funciona offline e não expõe sua conta do Drive.

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
- **Foto**: substitua `assets/img/marlon-cunico.jpg` por outra na proporção 4:5 (ex.: 640×800 px). O nome do arquivo precisa continuar igual.
- **Imagem de compartilhamento**: `assets/img/og-image.png` (1200×630) é o card que aparece ao colar o link no LinkedIn ou no WhatsApp. Se mudar cargo ou números, vale refazer.
- **Cores e espaçamentos**: as variáveis no topo de `assets/css/style.css` (`--navy`, `--teal`, `--surface`…). Trocar `--teal` muda o acento do site inteiro.
- **Uma seção nova**: copie um `<section class="section">` inteiro, troque o `id` e acrescente o link correspondente no `<nav>`.
- **Ordem das seções**: recortar e colar o bloco `<section>` inteiro. Nada depende da ordem.

O site funciona sem JavaScript (o menu móvel e o destaque do menu são o único uso) e imprime em PDF limpo — `Ctrl/Cmd + P` gera uma versão sem menu e sem fundos escuros.

---

## Verificações rápidas depois de publicar

1. Abra no celular — o menu vira botão, as colunas empilham.
2. Cole `https://www.marloncunico.com` no LinkedIn ou no WhatsApp e veja se a imagem de compartilhamento aparece.
3. Clique nos cinco botões de contato e abra o currículo numa janela anônima — é assim que o headhunter vai abrir.
4. Teste o `/en/` e o botão PT/EN nos dois sentidos.
5. Rode o [Rich Results Test](https://search.google.com/test/rich-results) na home — os dados estruturados `Person` devem ser reconhecidos.
