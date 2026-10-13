# Explicação da barra de navegação

Este documento descreve a barra de navegação (*navbar*) existente na página inicial. Foi escrito para acompanhar este excerto de HTML e pode ser reutilizado noutros projectos Bootstrap.

```html
<nav class="navbar navbar-expand-sm navbar-light" id="barraNavegacao">
  <div class="container-fluid">
    <a
      class="navbar-brand position-absolute start-50 translate-middle-x"
      id="paginaInicial"
      href=""
    >Homepage</a>

    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#collapsibleNavbar"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="collapsibleNavbar">
      <ul class="navbar-nav">
        <!-- itens do menu -->
      </ul>
    </div>
  </div>
</nav>
```

## Índice rápido

- [`<nav>`](#nav)
- [`navbar`](#navbar)
- [`navbar-expand-sm`](#navbar-expand-sm)
- [`navbar-light`](#navbar-light)
- [`container-fluid`](#container-fluid)
- [Link da marca / Homepage](#link-da-marca-homepage)
- [`navbar-toggler` e menu colapsável](#navbar-toggler-e-menu-colapsável)
- [Itens e links do menu](#itens-e-links-do-menu)
- [`dropdown`](#dropdown)

<a id="nav"></a>

## `<nav>`

`<nav>` é um elemento semântico de HTML: indica que o seu conteúdo é uma zona de navegação. Não cria, por si só, o aspecto visual de uma barra; esse aspecto é fornecido pelas classes Bootstrap.

Usar `<nav>` em vez de um simples `<div>` ajuda leitores de ecrã, motores de pesquisa e outros programas a reconhecerem que estes links permitem navegar pelo site. É normalmente a escolha certa para o menu principal de uma página.

No código, o atributo `id="barraNavegacao"` identifica este `<nav>` de forma única. Pode ser usado para:

- aplicar estilos CSS específicos, por exemplo `#barraNavegacao { ... }`;
- seleccioná-lo em JavaScript;
- criar um link directo para a barra, por exemplo `pagina.html#barraNavegacao`.

<!-- [[navbar|Explicação da navbar]] -->

## navbar

`navbar` é a classe base de uma barra de navegação Bootstrap. Dá ao elemento a estrutura e os estilos necessários para funcionar como navbar: alinhamento dos elementos, espaçamentos, comportamento adequado dos links e variáveis de cores próprias da componente.

Sozinha, esta classe cria a base da barra, mas não define em que tamanho de ecrã o menu se fecha nem a variante de cores. Por isso é combinada com `navbar-expand-sm` e, neste caso, `navbar-light`:

```html
<nav class="navbar navbar-expand-sm navbar-light">
```

Em Bootstrap, é normal combinar várias classes num mesmo elemento: cada uma trata de uma responsabilidade diferente.

## navbar-expand-sm

`navbar-expand-sm` controla quando os links da navbar aparecem todos expandidos e quando passam para o modo compacto com botão de menu.

- Em ecrãs com largura **igual ou superior a `sm`** (a partir de 576 px), o menu é mostrado aberto, habitualmente numa linha horizontal.
- Em ecrãs **inferiores a `sm`**, os links ficam escondidos inicialmente e o botão `navbar-toggler` permite mostrá-los ou escondê-los.

O sufixo `sm` refere-se ao *breakpoint* pequeno do Bootstrap. Se a expansão só devesse acontecer em ecrãs maiores, poderiam ser usadas, por exemplo, `navbar-expand-md`, `navbar-expand-lg` ou `navbar-expand-xl`.

Exemplo:

```html
<!-- O menu só fica horizontal a partir de 992 px. -->
<nav class="navbar navbar-expand-lg">
```

Esta classe trabalha directamente com `collapse`, `navbar-collapse` e `navbar-toggler`: ela define as regras visuais responsivas; as outras classes e os atributos `data-bs-*` permitem abrir e fechar o conteúdo no telemóvel.

## navbar-light

`navbar-light` era a classe tradicional do Bootstrap para uma navbar sobre fundo claro: definia cores escuras para texto, links e ícone do botão, de modo a haver contraste.

No Bootstrap 5.3 e versões posteriores, a forma recomendada de definir o modo de cor passou a ser o atributo `data-bs-theme`. Para uma navbar clara, use:

```html
<nav class="navbar navbar-expand-sm" data-bs-theme="light">
```

Com a versão Bootstrap 5.3.8 que está referida no ficheiro, `navbar-light` pode não produzir o efeito esperado. `data-bs-theme="light"` é a opção mais explícita e actual. Para uma navbar escura, use `data-bs-theme="dark"` e um fundo com contraste, por exemplo:

```html
<nav class="navbar navbar-expand-sm bg-dark" data-bs-theme="dark">
```

<!-- [[container-fluid|Explicação do contentor]] -->

## container-fluid

`container-fluid` é um contentor Bootstrap que ocupa 100% da largura disponível. Neste caso, contém a marca, o botão de menu e a área colapsável.

Além de ocupar toda a largura, aplica espaçamentos laterais consistentes. Isso evita que os elementos fiquem encostados às extremidades da janela.

Diferença principal:

```html
<!-- Largura total da janela. -->
<div class="container-fluid">...</div>

<!-- Largura máxima variável conforme o tamanho do ecrã. -->
<div class="container">...</div>
```

`container-fluid` é adequado aqui porque a navbar deve ocupar toda a largura. Se se quisesse limitar o conteúdo a uma largura máxima, poderia usar-se `container`.

<!-- [[homepage|Explicação do link Homepage]] -->

## Link da marca / Homepage

O elemento seguinte é um link (`<a>`) que funciona como a marca da navbar e é visualmente centrado:

```html
<a
  class="navbar-brand position-absolute start-50 translate-middle-x"
  id="paginaInicial"
  href=""
>Homepage</a>
```

O atributo `id="paginaInicial"` dá um identificador único a este link. Pode servir para CSS, JavaScript ou para criar uma âncora como `#paginaInicial`.

`href` define o destino do link. Com `href=""`, o navegador navega para o URL actual — na prática, costuma recarregar a mesma página. Se a intenção for voltar explicitamente à página inicial, é mais claro usar, por exemplo:

```html
<a class="navbar-brand" href="index.html">Homepage</a>
```

### navbar-brand

`navbar-brand` identifica o nome, logótipo ou ligação principal da navbar. Bootstrap aplica-lhe tipografia e espaçamento adequados, fazendo com que se destaque dos links normais do menu.

Pode conter texto, uma imagem ou ambos:

```html
<a class="navbar-brand" href="index.html">
  <img src="images/logo.svg" alt="Nome da organização" height="32">
</a>
```

No código actual, o texto `Homepage` é a marca. A classe não decide a sua posição no centro; essa parte é feita pelas três classes seguintes em conjunto.

### position-absolute

`position-absolute` aplica `position: absolute` ao elemento. Um elemento com esta posição deixa de ocupar espaço normal no fluxo da página e pode ser colocado com classes como `top-0`, `start-0`, `end-0` e `start-50`.

Na navbar, isto permite que a marca seja centrada sem depender da largura dos links que existem à esquerda ou à direita. O elemento é posicionado em relação ao ancestral posicionado mais próximo; neste caso, a própria `.navbar` fornece normalmente essa referência.

Como o elemento deixa o fluxo normal, deve ser usado com cuidado: em ecrãs estreitos, uma marca larga pode sobrepor-se ao botão do menu ou aos restantes elementos.

### start-50

`start-50` coloca a margem inicial do elemento a 50% da largura do contentor de referência. Em páginas de escrita da esquerda para a direita, como esta, `start` corresponde ao lado esquerdo.

Simplificando, aplica aproximadamente:

```css
left: 50%;
```

Por si só, esta classe colocaria o **lado esquerdo** da palavra `Homepage` no centro. Por isso ainda é necessária `translate-middle-x`.

### translate-middle-x

`translate-middle-x` desloca o elemento horizontalmente em -50% da sua própria largura. Equivale, de forma simplificada, a:

```css
transform: translateX(-50%);
```

Combinada com `start-50`, obtém-se um centramento horizontal real:

1. `start-50` leva o lado esquerdo do link até ao centro do contentor;
2. `translate-middle-x` recua o link metade da sua própria largura;
3. o centro do link fica alinhado com o centro da navbar.

Não confundir com `translate-middle`, que move o elemento tanto no eixo horizontal como no vertical. Neste caso usa-se `translate-middle-x` porque só se pretende centrar na horizontal.

Exemplo reutilizável:

```html
<div class="position-relative">
  <span class="position-absolute start-50 translate-middle-x">Texto centrado</span>
</div>
```

## navbar-toggler e menu colapsável

Em ecrãs inferiores a `sm`, `navbar-expand-sm` faz com que o menu possa ser recolhido. O botão responsável por abrir e fechar esse menu é:

```html
<button
  class="navbar-toggler"
  type="button"
  data-bs-toggle="collapse"
  data-bs-target="#collapsibleNavbar"
>
  <span class="navbar-toggler-icon"></span>
</button>
```

<!-- [[navbar-toggler|Explicação do botão de menu]] -->

### navbar-toggler

`navbar-toggler` aplica o estilo Bootstrap ao botão de menu. O seu conteúdo, `navbar-toggler-icon`, desenha o ícone habitual de três linhas. O aspecto deste ícone deve ter contraste com o modo de cor da navbar, definido actualmente por `data-bs-theme`.

`type="button"` é importante se a navbar estiver dentro de um formulário: impede que o clique seja tratado como submissão do formulário.

### data-bs-toggle e data-bs-target

Estes atributos activam o componente JavaScript `Collapse` do Bootstrap:

- `data-bs-toggle="collapse"` diz que o botão controla conteúdo que pode ser recolhido ou expandido;
- `data-bs-target="#collapsibleNavbar"` indica qual é o elemento a controlar. O valor é um selector CSS que aponta para o `id="collapsibleNavbar"`.

O JavaScript do Bootstrap tem de estar carregado para este comportamento funcionar. O ficheiro já inclui `bootstrap.bundle.min.js`, que contém o código necessário.

Por acessibilidade, recomenda-se acrescentar um nome ao botão e o estado inicial:

```html
<button
  class="navbar-toggler"
  type="button"
  data-bs-toggle="collapse"
  data-bs-target="#collapsibleNavbar"
  aria-controls="collapsibleNavbar"
  aria-expanded="false"
  aria-label="Abrir menu de navegação"
>
  <span class="navbar-toggler-icon"></span>
</button>
```

<!-- [[collapsible-navbar|Explicação do menu recolhível]] -->

### collapse e navbar-collapse

```html
<div class="collapse navbar-collapse" id="collapsibleNavbar">
```

- `collapse` torna esta área recolhível. Em ecrãs pequenos, fica oculta até o botão ser accionado;
- `navbar-collapse` adapta a área para uso dentro de uma navbar, incluindo o comportamento de expansão definido por `navbar-expand-sm`;
- `id="collapsibleNavbar"` liga este elemento ao botão através de `data-bs-target="#collapsibleNavbar"`.

O valor do `id` e o texto depois de `#` em `data-bs-target` têm de ser exactamente iguais. Se um deles mudar, o botão deixa de controlar o menu.

## Itens e links do menu

A lista que contém as opções da navbar é:

```html
<ul class="navbar-nav">
  <li class="nav-item">
    <a class="nav-link" href="loja.html">Cursos</a>
  </li>
</ul>
```

<!-- [[navbar-nav|Explicação da lista de navegação]] -->

### navbar-nav

`navbar-nav` prepara a lista `<ul>` para conter links de uma navbar. Quando a navbar está expandida, os itens são apresentados de forma adequada numa linha; quando está recolhida, adaptam-se ao menu vertical.

### nav-item

`nav-item` é colocada em cada `<li>`. Representa uma opção individual do menu e permite ao Bootstrap tratar correctamente o espaçamento e variantes como dropdowns.

### nav-link

`nav-link` é aplicada ao `<a>` clicável. Define o espaçamento, cores e estados de interacção coerentes com a navbar. O destino de cada ligação é definido por `href`, por exemplo `href="loja.html"` para abrir a página dos cursos.

Para marcar a página actual, pode acrescentar-se `active` e atributos de acessibilidade:

```html
<a class="nav-link active" aria-current="page" href="index.html">Início</a>
```

<!-- [[dropdown-logo|Explicação do item com o logótipo]] -->

## dropdown

No HTML fornecido existe este item:

```html
<li class="nav-item dropdown" id="linkDropdown">
  <img src="images/logo/cesae-digital-logo.svg" alt="">
</li>
```

`dropdown` identifica um item que **pode** conter um menu pendente. No estado actual, porém, este não é ainda um dropdown funcional: há apenas uma imagem, sem botão/ligação com `dropdown-toggle` e sem a lista `dropdown-menu`.

O `id="linkDropdown"` apenas identifica o item; não cria por si só um menu pendente.

Um dropdown funcional pode ter esta estrutura:

```html
<li class="nav-item dropdown">
  <button
    class="nav-link dropdown-toggle"
    type="button"
    data-bs-toggle="dropdown"
    aria-expanded="false"
  >
    Mais opções
  </button>

  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="perfil.html">Perfil</a></li>
    <li><a class="dropdown-item" href="contactos.html">Contactos</a></li>
  </ul>
</li>
```

Aqui, `dropdown-toggle` mostra o indicador visual e `data-bs-toggle="dropdown"` activa o comportamento JavaScript. `dropdown-menu` contém os itens que aparecem quando o utilizador abre o menu.

<!-- [[link-cursos|Explicação do link Cursos]] -->

## Link Cursos

```html
<li class="nav-item">
  <a class="nav-link" href="loja.html">Cursos</a>
</li>
```

`nav-item` identifica este `<li>` como uma opção da navbar. `nav-link` aplica a aparência e os espaçamentos próprios de uma ligação de navegação Bootstrap. O atributo `href="loja.html"` abre o ficheiro `loja.html`, relativo à pasta da página actual.

<!-- [[link-parceiros|Explicação do link Parceiros]] -->

## Link Parceiros

```html
<li class="nav-item">
  <a class="nav-link" href="media.html">Parceiros</a>
</li>
```

Tem a mesma estrutura do link Cursos. A diferença é o destino: `href="media.html"` abre a página `media.html`.

<!-- [[link-formulario|Explicação do link Formulário]] -->

## Link Formulário

```html
<li class="nav-item">
  <a class="nav-link" href="formulario.html">Formulario</a>
</li>
```

Também usa `nav-item` e `nav-link`. `href="formulario.html"` aponta para a página do formulário e `Formulario` é o texto visível da ligação.

## Como testar os links

Os comentários do ficheiro HTML de teste usam uma referência com o identificador `navbar`; a âncora com o mesmo identificador encontra-se antes da secção **navbar** deste documento.

Abra `navbar-com-links.html`, mantenha `Ctrl` premido e clique no texto azul do comentário. A extensão deverá abrir este ficheiro na âncora correspondente. Os comentários são ignorados pelo navegador, pelo que não alteram o aspecto nem o funcionamento da página.
