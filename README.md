# Crie um site com Hugo

## O que é Hugo?
Hugo é um gerador de site estático (SSG) que está ganhando força no mundo da construção de sites. Como um site estático, existem algumas limitações em suas funcionalidades. Mas aqui estão algumas das razões pelas quais eu amo usar Hugo:

- muito rápido
- facilmente personalizável
- simples de entender e começar
- integração perfeita com APIs de terceiros
- eu mencionei que é rápido?

Neste post, compartilharei como construir um blog simples e funcional que você pode estilizar com um pouco de CSS usando o Bootstrap 5.
```
Usar um framework como Bootstrap ou Bulma torna a construção de sites muito mais rápida para que você possa se concentrar na criação de conteúdo!
```

### Por que Hugo é rápido?

1. Escrito em Go (Golang)
- Go é uma linguagem de programação criada no Google que é expressiva, leve, concisa e eficiente. Uma de suas melhores características é o processamento simultâneo, onde várias linhas de código são executadas em um único momento. Por isso é tão rápido!
2. Sem banco de dados ou dependências
-Um site estático não precisa de um banco de dados. São apenas códigos e mídias como fotos, vídeos ou sons. Os sites Hugo também são executados sem dependências em tempos de execução caros, como PHP ou Python.

Sites estáticos não são adequados para construir todo tipo de site. No entanto, Hugo é melhor para construir:
- blogs,
- sites da empresa (comércio eletrônico),
- sites de portfólio,
- sites de documentação,
- site com uma única página de destino,
- ou sites com milhares de páginas.

Se você gostaria de construir qualquer um dos tipos de site acima, continue lendo. Comente se você gostaria que eu compartilhasse outros tipos de tutorial.

Esta é a prévia do site que estamos construindo neste tutorial:
https://heksagonnet.github.io/four/

## Instalar Hugo

Vamos começar instalando o Hugo em nosso computador. Você pode conferir o site deles para diferentes métodos de instalação ou com base no seu dispositivo. Para este exemplo, vou baixar e extrair o arquivo zip em uma máquina Windows 10.

1. Crie o diretório Hugo
Abra o Windows Explorer e crie uma nova pasta no `C:\` diretório chamado Hugo (H maiúsculo para Hugo) ou `C:\Hugo`. Dentro da pasta Hugo, crie um arquivo chamado bin ou `C:\Hugo\bin`

2. Baixando Hugo
Antes de fazer o download, você precisa saber se o seu computador está em um sistema operacional de 32 bits ou 62 bits nas especificações do dispositivo nas configurações do sistema. Para fazer isso, abra o Windows Explorer e clique com o botão direito do mouse `This PC` e clique em Propriedades (ou você pode clicar com o botão direito do mouse no botão Iniciar e clicar em Sistema).
Em seguida, você pode prosseguir para a página de lançamentos para baixar a respectiva pasta compactada na pasta `C:\Hugo\bin` criada anteriormente.
Clique com base no sistema operacional do seu computador `hugo.exe`. Em seguida , prossiga para extrair `LICENSE` e `README.md` para o `C:\Hugo\bin` que criamos anteriormente.

3. Adicione Hugo às configurações de PATH do Windows
Depois de mover os arquivos, você precisará adicionar Hugo às configurações de caminho do Windows. Vá para as Especificações do dispositivo onde você encontrou seu tipo de sistema operacional (32 bits ou 64 bits) anteriormente.
Clique com o botão direito do mouse no botão Iniciar e clique em Sistema. Em seguida, vá para Configurações avançadas do sistema. Clique em Variáveis ​​de Ambiente. Na seção User Variables (superior), clique duas vezes em Path.
Em seguida, clique em Novo e digite `C:\Hugo\bin` onde `hugo.exe` está localizado no seu dispositivo.
Após terminar de digitar, clique em Enter. Em seguida, clique em OK para sair em todas as janelas.
Para verificar se sua instalação está correta, abra o Prompt de Comando (Clique em Iniciar ou no botão Windows, digite `cmd` e clique em Enter). Quando você digita `hugo help` e clica em enter, deve aparecer uma saída do comando.
Ao digitar `path` e clicar em Enter, entre os caminhos disponíveis, você também deverá ver:
```
C:\Hugo\bin
```

## Criando seu site Hugo
Estarei usando o Visual Studio Code, um editor de código fonte da Microsoft para Windows, Linus ou MacOS. Portanto, se você não estiver usando o Windows, não se preocupe, você ainda pode acompanhar o comando e a interface será semelhante.

1. Crie uma pasta
Como você instalou o Hugo em suas configurações de PATH, você pode usá-lo em qualquer lugar em seu dispositivo Windows (se estiver tendo problemas para colocar Hugo em seu PATH, execute o comando create new hugo site em `C:\Hugo\bin` vez disso).
Eu criei uma pasta chamada MyBlog na pasta Documentos.

2. Editor de código-fonte aberto
Digite cmd na barra de endereços.
Quando o prompt de comando aparecer, digite `code .` assim e clique em Enter:
```
C:\Documents\MyBlog>code .
```

3. Crie um novo site Hugo
Uma coisa boa sobre o Visual Studio Code é que ele vem com seu próprio Terminal.

Em seguida, digite `hugo new site myblog` no Terminal ( myblog é apenas um nome de pasta. Você pode substituí-lo por qualquer nome que desejar. Ele não determina o nome do seu site ou outros valores):
```
C:\Documents\MyBlog>hugo new site myblog
```
Ao clicar em Enter, alguns arquivos e pastas são criados para você da seguinte maneira:
```
.
├── archetypes
│   └── default.md
├── content
├── data
├── layouts
├── static
├── themes
└── config.toml
```
Parabéns, seu novo site Hugo está construído! Vamos começar esta aventura!

## Criando seu próprio tema
Como o Hugo é um gerador de site estático, você precisaria empregar seu conhecimento básico de HTML, CSS e JS para projetar sua aparência e seu funcionamento.

Aqui (https://www.heksagon.net/web-design/how-to-start-with-html/) está uma introdução a esse tópico.

Para este tutorial, estamos mergulhando na criação de nosso próprio tema personalizável com a ajuda do Bootstrap 5. Se você gosta mais de temas prontos, há uma infinidade de belos temas Hugo de código aberto disponíveis na Hugo Themes Collection.

### Crie um tema de esqueleto Hugo
Hugo vem com um comando para criar um tema de esqueleto que usarei para desenvolver este blog. Fazer isso:

1. (Alterar Diretório) cd em meublog
```
C:\Documents\MyBlog>cd myblog
```

2. Use o comando hugo new theme e dê um nome ao seu tema. Vamos nomeá-lo `four`:
```
C:\Documents\MyBlog\myblog>hugo new theme four
```

3. Hugo criará seus novos arquivos de tema que se parecem com isso:
```
.
├── archetypes
│   └── default.md
├── content
├── data
├── layouts
├── resources
│   └── _gen
│       ├── assets
│       └── images
├── static
├── themes
│   └──  four
│           ├── archetypes
│           │   └── default.md
│           ├── layouts
│           │   ├── _default
│           │   │   ├── baseof.html
│           │   │   ├── list.html
│           │   │   └── single.html
│           │   ├── partials
│           │   │   ├── footer.html
│           │   │   ├── head.html
│           │   │   └── header.html
│           │   ├── 404.html
│           │   └── index.html
│           ├── static
│           │   ├── css
│           │   └── js
│           ├── LICENSE
│           └── theme.toml
└── config.toml
```

Na pasta `layouts`, repare que só vem `baseof.html` pré-preenchido. Se você estiver familiarizado com HTML, observe suas semelhanças. Mas com o Golang, ele vem com códigos de colchetes `{}`.

Hugo é projetado para que cada seção seja codificada separadamente (como parciais) e seja combinada para criar modelos html completos em todas as páginas do seu site ou quando você quiser. Isso é semelhante ao método de programação Python, onde emprega o método DRY (Don't Repeat Yourself).

## Instalar Bootstrap

Para usar o Bootstrap 5 em nosso site, vamos visitar o site deles para obter a documentação.

1. Crie uma nova pasta em sua pasta `four` de temas chamada `assets`. Em seguida, crie duas pastas chamadas `css` e `js` na pasta `assets`. Deve ficar assim:
```
four
    └── assets
            ├── css
            └── js
```

2. Baixe os arquivos CSS e JS compilados no site do Bootstrap. Extraia `bootstrap.min.css` para a pasta `css` e crie um novo arquivo chamado `style.css` para quaisquer alterações personalizadas que possamos ter. Da mesma forma, extraia `bootstrap.bundle.min.js` para a pasta `js` criada anteriormente. A estrutura deve ficar assim até agora:
```
four
    └── assets
            ├── css
            │   ├── bootstrap.min.css
            │   └── style.css
            └── js
                └── bootstrap.bundle.min.js
```

Adicione o seguinte código dentro de `style.css`:
```
section {
  min-height: 50vh;
}

#heroFour .carousel-item > img {
  height: 70vh;
  object-fit: cover;
  object-position: 50% 50%;
}
```

3. baseof.html

- Ao lado da tag html, adicione lang=“en” para seguir o Starter Template do Bootstrap.
- Estamos usando as funções de linha e colunas para criar uma barra lateral responsiva. Adicione um parcial chamado `sidebar.html`(crie um novo arquivo chamado `sidebar.html` na pasta parcial).
Adicione também uma chamada parcial `scripts.html` (crie um novo arquivo chamado `scripts.html` na pasta parcial também).
O seu `baseof.html` deve ficar assim:
```
<!DOCTYPE html>
<html lang="en">
  {{- partial "head.html" . -}}
  <body>
    {{- partial "header.html" . -}}
    <div class="container p-3">
      <div class="row">
        <div class="col-sm-7">{{- block "main" . }}{{- end }}</div>
        <div class="col-sm-5">{{- partial "sidebar.html" . -}}</div>
      </div>
    </div>
    {{- partial "footer.html" . -}} {{- partial "scripts.html" . -}}
  </body>
</html>
```

1. Para o parcial `scripts.html`, adicione o seguinte e clique em salvar:
```
{{ $bootstrapbundle := resources.Get "js/bootstrap.bundle.min.js" }}
<script src="{{ $bootstrapbundle.Permalink }}"></script>
<!-- Add your custom JS below this line -->
```

`$bootstrapbundle` é uma variável para recuperar o arquivo de ativos que está dentro da pasta de ativos. Esse método é especialmente útil se você quiser usar os recursos integrados do Hugo, como reduzir ou reduzir arquivos de impressão digital armazenados na pasta de ativos.

## head.html

Para o parcial `head.html`, adicione as seguintes dependências e clique em salvar:
```
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <!-- Generator -->
  {{- hugo.Generator }}

  <!-- Bootstrap CSS -->
  {{ $bootstrap := resources.Get "/css/bootstrap.min.css" }}
  <link rel="stylesheet" href="{{ $bootstrap.Permalink }}" as="style" />

  <!-- Fontawesome Icons -->
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"
    integrity="sha512-iBBXm8fW90+nuLcSKlbmrPcLa0OT92xO1BIsZ+ywDWZCvqsWgccV3gFoRBv0z+8dLJgyAHIhR35VZc2oM/gI1w=="
    crossorigin="anonymous"
    referrerpolicy="no-referrer"
  />

  <!-- Custom CSS -->
  {{ $style := resources.Get "/css/style.css" | minify | fingerprint }}
  <link rel="stylesheet" href="{{ $style.Permalink }}" as="style" />

  <!-- Title -->
  {{ $title := print .Title " | " .Site.Title }} {{ if .IsHome }}{{ $title =
  .Site.Title }}{{ end }}
  <title>{{ $title }}</title>

  <!-- Favicon -->
  <link rel="icon" href="{{- .Site.Params.favicon | default "favicon.ico" |
  absURL -}}" sizes="256x256"> {{ template "_internal/disqus.html" . }} {{
  template "_internal/google_news.html" . }} {{ template
  "_internal/google_analytics.html" . }} {{ template
  "_internal/google_analytics_async.html" . }} {{ template
  "_internal/opengraph.html" . }} {{ template "_internal/schema.html" . }} {{
  template "_internal/twitter_cards.html" . }}
</head>
```

### Variáveis

Como você pode ver, a variável `$style` é minificada e impressa. O Minify otimizará o tamanho dos seus arquivos e a impressão digital gerará números aleatórios após o seu `style.css` para manter seu site seguindo a última versão atualizada.

### Variáveis ​​do site e config.toml

Qualquer variável que comece com `.Site`, como `.Site.Title`, será chamada no `config.toml`. Isso significa que você pode ter um valor padronizado para todo o seu site no arquivo de configuração. Você também pode usar `config.yaml` ou `config.json` com base em sua preferência de idioma.

### Modelo

Também adicionei alguns modelos internos prontos para Hugo para os casos de uso mais comuns.

## header.html

Para o parcial `header.html`, adicione o seguinte e clique em salvar:
```
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="{{ "/" | relURL }}">{{ .Site.Title}}</a>

    <!-- Activated for mobile view -->
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <!-- Menu Start -->
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        {{ range .Site.Menus.main }}
        <li class="nav-item">
          {{ $text := print .Name | safeHTML }}
          <a class="nav-link" title="{{ $text }}" href="{{ .URL }}">
            {{ $text }}
          </a>
        </li>
        {{ end }}
      </ul>

      <div class="navbar-nav d-flex flex-row justify-content-around">
        {{ range .Site.Menus.social }}
        {{ $title := print .Title | safeHTML }}
        <a class="nav-link" title="{{ $title }}" href="{{ .URL }}">
          {{ $text := print .Name | safeHTML }}
          <i class="{{ $text }}"></i>
        </a>
        {{ end }}
      </div>
    </div>
    <!-- Menu End -->
  </div>
</nav>
```

## footer.html

Para o parcial `footer.html`, adicione o seguinte e clique em salvar:
```
<footer class="footer text-center bg-dark py-5 text-light">
  <!-- Change YourName to any name of your choice -->
  <p>Copyright &copy; {{ now.Format "2006"}} YourName</p>
  <p>
    Designed by
    <a class="link-secondary" href="https://www.heksagon.net/">Heksagon</a> with
    love ❤
  </p>
  <p>
    <a class="link-secondary" href="#">Back to top</a>
  </p>
</footer>
```

## sidebar.html

Para o parcial `sidebar.html`, adicione o seguinte e clique em salvar:
```
<div class="card mx-3 my-5 p-3">
  <h2>Sidebar</h2>
  <p>
    Add any function that you like in the <code>sidebar.html</code> partial.
  </p>
</div>
```

## 404.html

A página 404 é uma página para a qual os visitantes são redirecionados quando o URL após o nome do seu domínio é inválido. Para que ele carregue nessa lógica, é preciso que haja algumas customizações para diferentes servidores e automáticas em outros. Hugo também fornece algumas diretrizes para sites que atendem nesses ambientes:

- Páginas do GitHub e Páginas do GitLab.
- Apache.
- Nginx.
- Amazon AWS S3.
- Amazon Cloud Front.
- Servidor Caddie.
- Netlify.
- Site estático do Azure.
- Se você quiser apenas testá-lo na visualização ao vivo, basta acessar `http://localhost:1313/404.html`

Fora da pasta `partials`, nas pastas `layouts`, existem dois arquivos que foram criados que são `404.html` e `index.html`. No `404.html`, adicione o seguinte:
```
{{ define "main" }}
<section id="main" class="text-center d-flex flex-column justify-content-center">
    <h1>Page Not Found</h1>
    <div>
     <h1><a class="btn btn-lg btn-outline-secondary" href="{{ "/" | relURL }}">Go Home</a></h1>
    </div>
</section>
{{ end }}
```

## metadados.html

`index.html` que é colocado na pasta raiz do seu servidor web é amplamente conhecido como a página inicial. Antes de prosseguirmos com a criação da página inicial, na pasta parciais, crie um `metadata.html` para chamar a data do post do blog. Você também pode ter informações adicionais, como tags, nome do autor e muito mais. Mas para este tutorial, vamos apenas adicionar a data da postagem como metadados assim:
```
{{ $dateTime := .PublishDate.Format "2006-01-02" }} {{ $dateFormat :=
.Site.Params.dateFormat | default "Jan 2, 2006" }}
<i class="far fa-calendar-alt"></i>
<time datetime="{{ $dateTime }}">{{ .PublishDate.Format $dateFormat }}</time>
```

## index.html

A página inicial. Eu adicionei alguns modelos do Bootstrap para você começar o mais rápido possível. Edite para mostrar sua criatividade!
```
<!DOCTYPE html>
<html lang="en">
{{- partial "head.html" . -}}
<body>
{{- partial "header.html" . -}}

<!-- Hero Carousel -->
<section id="heroFour" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-indicators">
    <button type="button" data-bs-target="#heroFour" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
    <button type="button" data-bs-target="#heroFour" data-bs-slide-to="1" aria-label="Slide 2"></button>
    <button type="button" data-bs-target="#heroFour" data-bs-slide-to="2" aria-label="Slide 3"></button>
  </div>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="{{ "/img/hero1.webp" | relURL }}" class="d-block w-100" alt="...">
      <div class="carousel-caption d-md-block">
        <h1>Life is either a daring adventure or nothing at all</h1>
        <p>Helen Keller</p>
      </div>
    </div>
    <div class="carousel-item">
      <img src="{{ "/img/hero2.webp" | relURL }}" class="d-block w-100" alt="...">
      <div class="carousel-caption d-md-block">
        <h1>Traveling – it leaves you speechless, then turns you into a storyteller</h1>
        <p>Ibn Battuta</p>
      </div>
    </div>
    <div class="carousel-item">
      <img src="{{ "/img/hero3.webp" | relURL }}" class="d-block w-100" alt="...">
      <div class="carousel-caption d-md-block">
        <h1>Life’s a journey not a destination</h1>
        <p>Aerosmith</p>
      </div>
    </div>
  </div>
  <button class="carousel-control-prev" type="button" data-bs-target="#heroFour" data-bs-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#heroFour" data-bs-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>
</section>

<!-- Our Values -->
<section class="py-5">
  <h2 class="text-center">We are committed</h2>
  <div class="container">
    <div class="row align-items-center">
      {{ range .Site.Params.values }}
      <div class="col-12 col-sm-4 text-center py-5">
        <i class="{{ .iconclass }} "></i>
        <h2>{{ .title }}</h2>
        <p>{{ .description }}</p>
      </div>
      {{ end }}
    </div>
  </div>
</section>

<!-- Jumbotron -->
<section class="py-5 bg-warning">
  <div class="p-5 mb-4 rounded-3">

    <div class="container-fluid py-5">
      <h1 class="display-5 fw-bold">Custom jumbotron</h1>
      <p class="col-md-8 fs-4">You are able to create this jumbotron, similar to previous versions of Bootstrap.</p>
      <button class="btn btn-primary btn-lg" type="button">Button</button>
    </div>

    <div class="row align-items-md-stretch">

      <div class="col-md-6">
        <div class="h-100 p-5 text-white bg-dark rounded-3">
          <h2>Dark background</h2>
          <p>Swap the background-color utility and add a `.text-*` color utility to mix up the jumbotron look. Then, mix and match with your favourite choice.</p>
          <button class="btn btn-outline-light" type="button">More ...</button>
        </div>
      </div>

      <div class="col-md-6">
        <div class="h-100 p-5 bg-light border rounded-3">
          <h2>Add borders</h2>
          <p>You can also keep it light and add a border for some added definition to the boundaries of your content. </p>
          <button class="btn btn-outline-secondary" type="button">Be Creative</button>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- Blog Section -->
<section class="album py-5 bg-light">
  <div class="text-center py-5">
    <h2 class="fs-1">Blog</h2>
    <p class="fs-4 text-muted">Latest Article</p>
  </div>
  <div class="container">
    <div class="row d-flex justify-content-center">
      {{ range (.Paginator 3).Pages.ByPublishDate.Reverse }}
      <div class="col-sm-4 my-3">
        <div class="card shadow-sm">
          <img class="bd-placeholder-img card-img-top" width="100%" height="225" src="{{ .Params.cover.image }}" style="object-fit: cover;"></img>

          <div class="card-body">
            <h3 class="card-text">{{ .Title }}</h3>
            <p class="card-text">{{ partial "metadata.html" . }}: {{ .Params.description }}</p>
            <div class="d-flex justify-content-between align-items-center">
              <div class="btn-group">
                <a href="{{ .RelPermalink }}">
                <button type="button" class="btn btn-sm btn-outline-secondary"> View</button></a>
              </div>
              <div class="btn-group">
                {{ with .Params.tags }}
                {{ range . }}
                {{ $href := print (absURL "tags/") (urlize .) }}
                <a class="btn btn-sm btn-outline-secondary" href="{{ $href }}">{{ . }}</a>
                {{ end }}
                {{ end }}
              </div>
            </div>
          </div>
        </div>
      </div>
      {{ end }}
    </div>
    <p class="text-end">
      <a href="{{ "/posts/" | relURL }}">More...</a>
    </p>
  </div>
</section>

<!-- Contact Section -->
<section id="contact" class="py-5 bg-warning" style="background-image: url(/img/map-image.png);background-size: contain;background-repeat: no-repeat;">
  <div class="container">
    <div class="row">
      <div class="col-sm-6 d-flex align-items-center">
        <h2>Contact Us</h2>
      </div>
      <div class="col-sm-6">
        <form action="">
          <div class="m-3">
            <label for="exampleFormControlInput1" class="form-label">Email address</label>
            <input type="email" class="form-control" id="exampleFormControlInput1" placeholder="your@email.com">
          </div>
          <div class="m-3">
            <label for="exampleFormControlTextarea1" class="form-label">Your messsage here:</label>
            <textarea class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
          </div>
        </form>
      </div>
    </div>
  </div>
</section>

{{- partial "footer.html" . -}}
{{- partial "scripts.html" . -}}
</body>
</html>
```

## Seção de contato

Na seção de contato, o formulário aqui pode ser substituído por provedores de formulário, como `Formspree.io (https://formspree.io/)` ou `Formsubmit.io (https://formsubmit.io/)` , para que os visitantes do site possam entrar em contato com você. Também é possível codificar sua própria função PHP para receber submissões.

## config.toml

Este arquivo é usado para armazenar as principais informações sobre um site Hugo, integrar determinadas funcionalidades e imagens de chamadas. Todo o valor neste arquivo é ajustado com base nas necessidades do seu site. O mais importante é vincular com o tema que foi criado:
```
theme = "four"
```
BaseURL é o nome de domínio do seu site, title é o título do seu site, seu próprio `ID do Google Analytics (https://analytics.google.com/analytics/web/)` e seu próprio nome `abreviado do Disqus (https://disqus.com/)`. Aqui está um pequeno exemplo que usei para este tutorial do Hugo:

```
baseURL = "http://example.org/"
languageCode = "en-us"
title = "Four: Travel Blog"
theme = "four"
googleAnalytics = "UA-PROPERTY_ID/G-MEASUREMENT_ID"
disqusShortname = "yourdiscussshortname"

[params]
description = "Open Graph Description"
images = [ "/img/hero1.webp" ]
title = "Four: Travel Blog"
favicon = "img/world-map-pin.svg"

  [[params.values]]
  iconclass = "fas fa-pen text-primary fa-3x py-3"
  title = "Blog"
  description = "Dedicated to sharing insightful information"

  [[params.values]]
  iconclass = "fas fa-bolt text-primary fa-3x py-3"
  title = "Speed"
  description = "Our priority in getting the job done fast"

  [[params.values]]
  iconclass = "fas fa-comment text-primary fa-3x py-3"
  title = "Chat"
  description = "Keep in touch with us to know more"

[minify]
minifyOutput = true

[[menu.main]]
identifier = "blog"
name = "Posts"
url = "/posts/"
weight = 1

[[menu.main]]
identifier = "Contact"
name = "Contact"
url = "/#contact"
weight = 2

[[menu.main]]
identifier = "tags"
name = "Tags"
url = "/tags"
weight = 3

[[menu.social]]
name = "fab fa-twitter fa-2x link-info"
title = "Twitter"
url = "/"
weight = 1

[[menu.social]]
name = "fab fa-youtube fa-2x link-danger"
title = "Youtube"
url = "/"
weight = 2
```

## Imagens

As imagens são um dos elementos mais importantes de um site. Eles tornam seu site colorido e interessante. Se não for otimizado, também pode diminuir a velocidade de carregamento do seu site. Observe que neste exemplo, a maioria das imagens usadas está no formato webp.

Um pequeno artigo sobre como otimizar imagens para o formato WebP. (https://www.heksagon.net/web-design/how-to-optimize-your-website-with-webp-images/)

Na pasta estática do fourtema, crie uma nova pasta chamada `img` para manter as imagens do `config.toml` e `index.html`:
```
static
    ├── css
    ├── img
    │    ├── hero1.webp
    │    ├── hero2.webp
    │    ├── hero3.webp
    │    ├── map-image.png
    │    └── world-map-pin.svg
    └── js
```

## Layout padrão Hugo
Na pasta de layouts de temas, existe outra pasta chamada `_default` que armazena os layouts básicos do Hugo:

1. `list.html` é o modelo de layout para listar todas as postagens do blog
2. `single.html` é o modelo de layout para listar um único post
3. `terms.html` é o modelo de layout para listar taxonomias. Nestes exemplos, apenas a `tags` taxonomia é usada.

Cada layout é estilizado com base em classes de Bootstrap adequadas:

### lista.html
```
{{ define "main" }}
<h1>{{ .Title }}</h1>
<div class="row d-flex justify-content-center">
  {{ range .Pages.ByPublishDate.Reverse }}
  <div class="col-lg-6 my-3">
    <div class="card shadow-sm">
      <img class="bd-placeholder-img card-img-top" width="100%" height="225" src="{{ .Params.cover.image }}" style="object-fit: cover;"></img>
      <div class="card-body">
        <h3 class="card-text">{{ .Title }}</h3>
        <p class="card-text">{{ partial "metadata.html" . }}: {{ .Params.description }}</p>
        <div class="d-flex justify-content-between align-items-center">
          <div class="btn-group">
            <a href="{{ .RelPermalink }}">
            <button type="button" class="btn btn-sm btn-outline-secondary"> View</button></a>
          </div>
          <div class="btn-group">
            {{ with .Params.tags }}
            {{ range . }}
            {{ $href := print (absURL "tags/") (urlize .) }}
            <a class="btn btn-sm btn-outline-secondary" href="{{ $href }}">{{ . }}</a>
            {{ end }}
            {{ end }}
          </div>
        </div>
      </div>
    </div>
  </div>
{{ end }}
</div>
{{ end }}
```

### single.html
```
{{ define "main" }}
<h1>{{ .Title }}</h1>
<img
  class="w-100"
  src="{{ .Params.cover.image }}"
  alt="{{ .Params.cover.alt }}"
/>
<p class="text-center">{{ .Params.cover.caption }}</p>

<div class="row text-center">
  <div class="col">{{ partial "metadata.html" . }}</div>
  <div class="col">
    <div class="btn-group">
      {{ with .Params.tags }} {{ range . }} {{ $href := print (absURL "tags/")
      (urlize .) }}
      <a class="btn btn-sm btn-outline-secondary" href="{{ $href }}">{{ . }}</a>
      {{ end }} {{ end }}
    </div>
  </div>
</div>
<br /><br />
{{ .Content }} {{- partial "disqus.html" . -}} {{ end }}
```

### terms.html
```
{{- define "main" }}
<section class="row">
  <div class="has-text-centered">
    <h1 class="fs-1">{{ .Title }}</h1>
    <p>{{ .Description }}</p>
  </div>
  <div class="col">
    <div class="container">
      <ul class="list-group">
        {{- $type := .Type }} {{- range $key, $value := .Data.Terms.Alphabetical
        }} {{- $name := .Name }} {{- $count := .Count }} {{- with $.Site.GetPage
        (printf "/%s/%s" $type $name) }}
        <li class="list-group-item btn btn-sm btn-outline-secondary">
          <a
            class="stretched-link text-decoration-none link-secondary fs-4"
            href="{{ .Permalink }}"
            >{{ .Name }}
            <sup
              ><strong class=""><sup>{{ $count }}</sup></strong></sup
            ></a
          >
        </li>
        {{- end }} {{- end }}
      </ul>
    </div>
  </div>
</section>
{{- end }}{{/* end main */ -}}
```

## Seção de comentários
Observe em `single.html`, há uma parcial que não foi criada, `disqus.html`. Esta parcial já está incluída nos templates internos declarados no `head.html`. No entanto, Hugo recomenda adicionar a seguinte parcial chamada `disqus.html` para evitar discussões indesejadas com a conta Disqus associada no ambiente localhost:
```
<div id="disqus_thread"></div>
<script type="text/javascript">
  ;(function () {
    // Don't ever inject Disqus on localhost--it creates unwanted     // discussions from 'localhost:1313' on your Disqus account...     if (window.location.hostname == 'localhost') return

    var dsq = document.createElement('script')
    dsq.type = 'text/javascript'
    dsq.async = true
    var disqus_shortname = '{{ .Site.DisqusShortname }}'
    dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js'
    ;(
      document.getElementsByTagName('head')[0] ||
      document.getElementsByTagName('body')[0]
    ).appendChild(dsq)
  })()
</script>
<noscript
  >Please enable JavaScript to view the
  <a href="https://disqus.com/?ref_noscript"
    >comments powered by Disqus.</a
  ></noscript
>
<a href="https://disqus.com/" class="dsq-brlink"
  >comments powered by <span class="logo-disqus">Disqus</span></a
>
```

Se você gosta de usar outros provedores de comentários sugeridos por Hugo , você pode

- remova o modelo interno do Disqus em `head.html`
- remova o nome abreviado do Disqus `config.toml` e
- mude o parcial `single.html` para um provedor de comentários de sua escolha

## Conteúdo do blog

### Escreva um blog
Este projeto de blog está quase completo. Agora execute o seguinte no terminal:
```
C:\Documents\MyBlog\myblog>hugo new posts/post1.md
```

Este comando cria uma nova pasta `posts` dentro da pasta `content` com um arquivo markdown chamado `post1.md`:
```
---
title: 'Post1'
date: 2021-04-01T23:11:13Z
draft: true
---
```

Essas três variáveis ​​são chamadas de `Front Matter` e são baseadas no modelo na pasta `default.md` da pasta `archetypes`. Você pode ajustar seus padrões lá para que, ao executar `hugo new`, o modelo desejado apareça. Vou apenas ajustar `post1.md` para ser assim:
```
---
title: 'My First Post'
date: 2021-04-01T23:11:13Z
draft: true
tags: ['Africa', 'adventure']
description: 'This is the first post description'
images: ['/img/post1.webp']
cover:
  image: '/img/post1.webp'
  alt: 'This is a random image from Unsplash'
  caption: 'This is a random image from Unsplash'
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Pellentesque eu tincidunt tortor
aliquam nulla facilisi cras fermentum odio. A erat nam at lectus urna duis. Sed
velit dignissim sodales ut eu sem. Lectus urna duis convallis convallis tellus.
Diam sit amet nisl suscipit adipiscing bibendum est. Sed felis eget velit
aliquet sagittis id consectetur. Vulputate dignissim suspendisse in est ante in
nibh mauris cursus. Morbi quis commodo odio aenean. Mollis nunc sed id semper
risus in hendrerit gravida rutrum. Ac ut consequat semper viverra nam. Hac
habitasse platea dictumst vestibulum rhoncus. Amet porttitor eget dolor morbi
non. Justo eget magna fermentum iaculis eu non. Id eu nisl nunc mi ipsum
faucibus vitae aliquet nec. Aliquam id diam maecenas ultricies. Non sodales
neque sodales ut etiam. Amet massa vitae tortor condimentum lacinia quis. Erat
imperdiet sed euismod nisi porta. Nisl suscipit adipiscing bibendum est
ultricies integer quis auctor. Viverra suspendisse potenti nullam ac. Tincidunt
id aliquet risus feugiat in. Varius quam quisque id diam vel. Egestas erat
imperdiet sed euismod nisi. Scelerisque felis imperdiet proin fermentum leo vel
orci porta non. Ut faucibus pulvinar elementum integer. Fermentum odio eu
feugiat pretium nibh ipsum consequat nisl.
```

### Imagens do blog
Crie um novo arquivo na pasta `static` principal chamado `img` e salve todas as suas imagens para seus posts aqui. Isso é para segregar o conteúdo do seu blog e as imagens do seu tema para facilitar a edição e o gerenciamento do site mais tarde.
```
.
├── archetypes
│    └── default.md
├── content
├── data
├── layouts
├── static
│    └── img
│         └── post1.webp
├── themes
└── config.toml
```

### Visualização ao vivo

Por fim, a hora de testar seu site em um ambiente web. Hugo vem com um recurso de visualização ao vivo integrado com o servidor Hugo. Basta executar o seguinte comando no terminal (-D está com os rascunhos habilitados para visualizar nosso primeiro post elaborado):
```
C:\Documents\MyBlog\myblog>hugo server -D
```

Vá para qualquer navegador da Web e execute `http://localhost:1313/` . Você deve ser capaz de ver e explorar seu site concluído agora. Salve depois de fazer qualquer alteração para ver a alteração ocorrendo ao vivo.

## Implantar em um site ao vivo

Depois de fazer as alterações e desejar que seu site seja acessível a partir do nome de domínio adquirido, aqui estão as etapas:

### 1. Compre um nome de domínio e hospedagem
Se você planeja monetizar seu site ou estabelecer uma autoridade, ter seu próprio domínio é o caminho a percorrer. Aqui estão alguns provedores de hospedagem na web recomendados que me ajudam a ganhar uma pequena comissão se você se registrar com esses links:

Para hospedagem gratuita na web para sites estáticos, pode conferir os seguintes links:

- Páginas do Github - https://pages.github.com
- Netlify - https://www.netlify.com/
- 000WebHost - https://www.000webhost.com/
- Firebase - https://firebase.google.com/
- Google Cloud - https://cloud.google.com/

### 2. draft: false

Altere a matéria frontal de rascunho verdadeiro para falso e verifique todas as funções, imagens e trabalhos de estilo na visualização ao vivo.

### 3. Gerar Site Estático

Quando tudo estiver pronto para produção, execute o seguinte comando:
```
C:\Documents\MyBlog\myblog>hugo
```
Hugo irá gerar um site estático completo (HTML, CSS, JS) na pasta pública. Para tornar seu site ativo, você só precisa colocar o conteúdo dessa pasta na pasta raiz do seu site.

## Conclusão

Parabéns! Seu site agora está ATIVO na World Wide Web. Se você quiser que eu faça mais tutoriais como este, compartilhe na seção de comentários aqui. Este tutorial do Hugo cobre apenas o básico da criação de um blog funcional, mas simples, usando o Bootstrap 5.

## Fonte
https://www.heksagon.net/web-design/build-a-website-with-hugo/
