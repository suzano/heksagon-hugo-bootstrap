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











## Fonte
https://www.heksagon.net/web-design/build-a-website-with-hugo/
