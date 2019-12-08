**Conteúdo anterior**: [**Aprofundando no HTML**](./Aprofundando_no_html.md)

# Aprofundando no CSS

### Índice
+ [CSS e seletores úteis](#CSS-e-seletores-úteis)
    + [Seletores básicos](#Seletores-básicos)
    + [Seletores de descendência](#Seletores-de-descendência)
    + [Seletores irmãos](#Seletores-irmãos)
+ [Entendendo Flexbox](#Entendendo-Flexbox)
    + [Como colocar um elemento no centro da tela?](#Como-colocar-um-elemento-no-centro-da-tela?)
+ [Entendendo Grid](#Entendendo-Grid)

### CSS e seletores úteis
No CSS, você estiliza a estrutura e o conteúdo da sua página, mas para você conseguir estilizar bem, existem alguns seletores que podem ser úteis, e é isso que iremos ver agora.

#### Seletores básicos
Você já deve conhecer os seletores <code>*</code>, <code>.</code>, <code>#</code>, onde cada um representa, respectivamente, <code>all</code>, <code>class</code> e <code>id</code>. 

Vamos testar cada um da seguinte forma, vamos supor que você tenha a seguinte estrutura HTML:
```html
<body>
    <section id="app">
        <h1>Hello World</h1>
        <section class="links">
            <a href="#meulink">Meu Link</a>
            <a href="#meulink2">Meu Link 2</a>
        </section>
        <section class="links">
            <a href="#meulink3">Meu Link 3</a>
            <a href="#meulink4">Meu Link 4</a>
        </section>
    </section>
</body>
```

E as seguintes estruturas CSS:

<code>*</code>
```css
* { 
    background-color: red;
    color: white;
}
```
> Neste exemplo, toda a sua página terá fundo vermelho e texto branco.

<code>#</code>
```css
#app * {
    background-color: red;
    color: white;
}
```
> Neste exemplo, apenas os elementos dentro do id <code>app</code>, terão fundo vermelho e texto branco.

<code>.</code>
```css
.links * {
    background-color: red;
    color: white;
}
```
> Já neste exempo, apenas os elementos dentro da classe <code>links</code>, terão fundo vermelho e texto branco.
>
> Note que a diferença do <code>id</code> para <code>class</code>, é que cada <code>id</code> deve ser único na página, e podemos ter vários elementos com a mesma <code>class</code>.

#### Seletores de descendência
O primeiro seletor de descendência é um seletor básico também, onde você seleciona os filhos de um elemento, no exemplo do <code>.links *</code> vemos esse modelo de seletor funcionando. Vou dar um exemplo melhor:

```css
.links a {
    color: black;
    text-decoration: none;
}
```
> Neste exemplo, os links <code>a</code> dentro da classe <code>links</code>, terão cor preta e não terão mais o sublinhado.

Temos outros seletores de descendência que podem ser úteis no dia-a-dia, como o <code>></code> que serve para selecionar os filhos diretos de um elemento, e as pseudo-classes <code>:first-child</code> que seleciona o primeiro filho de um elemento, <code>:last-child</code> que seleciona o último filho de um elemento, e <code>:nth-child(n)</code> que seleciona um filho com base no valor passado em <code>n</code>. Vamos utilizar uma estrutura diferente dessa vez, para vermos melhor como eles funcionam:

\- **HTML**
```HTML
<body>
    <section id="app">
        <h1>Seletores</h1>
        <a href="">Link</a>
        <a href="">Link</a>
        <h2>Seletores de descendência</h2>
        <section>
            <h2>primeiro h2 da primeira section dentro de #app</h2>
            <h2>segundo h2 da primeira section dentro de #app</h2>
        </section>
        <section>
            <h2>h2 da segunda section dentro de #app</h2>
            <a href="">Link da segunda section dentro de #app</a>
        </section>
        <section>
            <h2>h2 da terceira section dentro de #app</h2>
            <a href="">Link da terceira section dentro de #app</a>
        </section>
    </section>
</body>
```

Vamos testar primeiro o seletor <code>></code>:
```css
#app > h2 {
    color: red;
}
```
> Neste exemplo, o único <code>h2</code> com cor vermelha é o filho dele, onde os outros <code>h2</code>'s seriam considerados "netos".


<code>:first-child</code>
```css
#app section h2:first-child {
    background-color: red;
}
```
> Neste exemplo, nós selecionamos apenas os primeiros <code>h2</code>'s de dentro das <code>section</code>'s.

<code>:last-child</code>
```css
#app section:last-child {
    background-color: red;
}
```
> Neste exemplo, nós selecionamos apenas a última <code>section</code> dentro de <code>#app</code>.

<code>:nth-child(n)</code>
```css
#app section h2:nth-child(2) {
    background-color: red;
}
```
> Neste exemplo, nós selecionamos apenas o segundo <code>h2</code> dentro das <code>section</code>'s.
>
> **Obs**: com o <code>:nth-child(n)</code>, nós temos uma dinâmica bem legal, onde se quisermos selecionar os elementos de 2 em 2, podemos colocar <code>:nth-child(2n)</code>, se quisermos de 3 em 3, é só mudar para <code>:nth-child(3n)</code>, e assim vai.

#### Seletores irmãos
Existem dois seletores para estilizar elementos na mesma camada, um deles é o <code>+</code> e o outro é <code>~</code>, onde cada um representa, respectivamente, o irmão que vem logo em seguida, se existir, e os irmãos. Vamos utilizar a mesma estrutura dos últimos exemplos:

<code>+</code>
```css
h2 + a {
    color: red;
}
```
> Neste exemplo, apenas os <code>a</code>'s, que vem em seguida dos <code>h2</code>'s, são selecionados.

<code>~</code>
```css
h2 ~ a {
    color: red;
}
```
> Neste exemplo, todos os <code>a</code>'s, que vierem depois, e na mesma camada que os <code>h2</code>'s, são selecionados.

#### Seletores de tipo
> Em breve

---

### Entendendo Flexbox
O Flexbox permite fazermos nossos layouts com muito mais facilidade, como por exemplo: colocar elementos um do lado do outro dando um espaçamento entre eles, colocar um de cada lado, ou coisas do tipo.

Você geralmente vai usar 4 propriedades para manipular seus layouts, que serão <code>display: flex</code>, <code>flex-direction</code>, <code>align-items</code> e <code>justify-content</code>.

#### Mas como funciona?
Devemos passar a ver o layout de uma forma diferente, iremos "componentizar" cada parte dele. Veja a imagem a seguir, e em seguida, irei lhe mostrar como fazer o cabeçalho, seguindo o Flexbox.

![Layout - Dribble](../images/flexbox.jpg)

Bom, poderiamos fazê-lo com <code>float</code>, ou com <code>text-align</code>, existem diversas formas de se fazer esse cabeçalho, mas como estou mostrando sobre flexbox, vamos entender esse conceito.

Para começar, você deve ter uma seção pai, e duas seções filhas, onde em uma você terá o conteúdo de "bem-vindo" e, no outro, você terá o nome do usuário e a foto.

Vamos para o código <br />
\- **HTML**:
```html
<header>
    <section id="welcome">
        <span class="welcome_title">Welcome Alec!</span>
        <p class="welcome_description">Welcome to Porto Business Management System.</p>
    </section>
    <section id="user">
        <span class="user_name">Alec Issigonis</span>
        <img class="user_photo" src="" alt="Alec Issigonis Photo">
    </section>
</header>
```

\- **CSS**:
```css
header {
    display: flex; /* Para colocar os elementos filhos em uma disposição flex */
    align-items: center; /* Para alinhar os elementos no centro da seção pai */
    justify-content: space-between; /* Para dar um espaçamento entre os elementos dentro da seção pai */
}
```
> Basicamente, o Flexbox é baseado na seção pai, então você deve sempre se basear em como você quer os elementos dispostos dentro da seção pai.

#### Como colocar um elemento no centro da tela?
Eu sei que uma hora você vai precisar disso, e é um conceito simples. Eu lhe disse antes, que o Flexbox é baseado na seção pai, então se você precisa de um elemento no centro da tela, você precisa colocar que a seção pai necessita ter 100% do tamanho da tela, então é so usar o tamanho <code>100vh</code> para a altura (height) e em seguida manipular o Flexbox com base na sua necessidade.

> O <code>display: flex</code> vai dizer à seção que os elementos dentro dela, devem ser dispostos de forma flexível.
>
> O <code>align-items</code> irá alinhar os elementos baseados na <code>flex-direction</code>, e como a <code>flex-direction</code> padrão é <code>row</code>, que alinha os elementos em linha, então o <code>align-items</code> irá alinhar os elementos na vertical. Se você mudar o <code>flex-direction</code> para <code>column</code>, então o <code>align-items</code> irá alinhar os elementos na horizontal. <br />
> <code>align-items: (baseline | center | flex-end | flex-start | stretch | inherit | initial | unset)</code>
>
> O <code>justify-content</code> irá também seguir o padrão do <code>flex-direction</code>, no entanto, ele seguirá a mesma direção. Então se o <code>flex-direction</code> for <code>row</code>, o <code>justify-content</code> irá alinhar os elementos na horizontal, já se for <code>column</code>, ele irá alinhar os elementos na vertical. <br />
> <code>justify-content: (baseline | center | end | first baseline | flex-end | flex-start | last baseline | left | right | safe | space-around | space-between | space-evenly | start | stretch | unsafe | inherit | initial | unset)</code>

---

### Entendendo Grid
O grid nos permite disponibilizar elementos de uma forma mais adequada, como se estivéssemos literalmente desenhando o layout no código. Vamos entender melhor.

#### Vamos começar desenhando um layout em grid
![SmartRetail by Anna Kirkizh](../images/grid.png)
Esse layout pode ser separado da seguinte maneira:
```text
container
    topo
        logo
        info
        cta
    corpo
        StoreEngine
        ReTrack
        SmartPick
```
Mas e no código?
\- **HTML**:
```html
<div class="container">
    <div class="topo">
        <div class="logo">
            <img src="logo.jpg" />
        </div>
        <div class="info">
            <span>8 800 350 66 15</span>
            <span>info@smartretail.pro</span>
        </div>
        <div class="cta">
            <button>Call-to-Action</button>
        </div>
    </div>
    <div class="corpo">
        <div class="storeengine">
            <div>
                <img src="imagem.jpg" />
            </div>
            <div>
                <h1><span>Store</span><span>Engine</span></h1>
                <h3>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Fuga ipsam iusto possimus cupiditate obcaecati.</h3>
            </div>
            <div>
                <a href=""><img src="button.jpg"> Action</a>
            </div>
        </div>
        <div class="retrack">
            <div>
                <img src="imagem.jpg" />
            </div>
            <div>
                <h1><span>Re</span><span>Track</span></h1>
                <h3>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Fuga ipsam iusto possimus cupiditate obcaecati.</h3>
            </div>
            <div>
                <a href=""><img src="button.jpg"> Action</a>
            </div>
        </div>
        <div class="smartpick">
            <div>
                <img src="imagem.jpg" />
            </div>
            <div>
                <h1><span>Smart</span><span>Pick</span></h1>
                <h3>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Fuga ipsam iusto possimus cupiditate obcaecati.</h3>
            </div>
            <div>
                <a href=""><img src="button.jpg"> Action</a>
            </div>
        </div>
    <div>
</div>
```
\- **CSS**:
```css
@import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');
* {
    font-family: 'Roboto', sans-serif;
    margin: 0;
    outline: none;
    padding: 0;
}
a {
    color: white;
    text-decoration: none;
    font-weight: 600;
}
body {
    background: #433e8d;
    height: 100vh;
    color: white;
}
.topo {
    align-items: center;
    box-sizing: border-box;
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    max-height: 80px;
    padding: 20px 60px;
}
.info {
    display: flex;
    font-weight: bold;
    justify-content: space-evenly;
}
.cta {
    text-align: right;
}
.cta button {
    background: white;
    border: 2px solid white;
    border-radius: 40px;
    box-sizing: border-box;
    color: #433e8d;
    cursor: pointer;
    font-weight: bold;
    padding: 8px 30px;
}
.corpo {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    padding: 0 60px;
}
.corpo a img {
    margin-right: 10px;
}
.corpo div:hover {
    background: white;
}
.corpo div:hover h1 span:first-child {
    color: #0086fb;
}
.corpo div:hover h1 span:last-child {
    color: #433e8d;
}
.corpo div:hover h3 {
    color: #0e1921;
}
.corpo div:hover a {
    color: #433e8d;
}
.storeengine, .retrack, .smartpick {
    display: grid;
    grid-template-rows: 1.3fr 0.5fr 1.3fr;
    height: 100%;
    align-items: center;
    padding: 0 60px;
}
.corpo div div h3 {
    margin-top: 30px;
}
.corpo div div:last-child {
    align-items: center;
    display: flex;
    height: 100%;
}
```
---


> **Referências:** <br />
>
> CSS e seletores úteis <br />
> [Os 30 Seletores CSS Que Você Deve Memorizar - Tuts+](https://code.tutsplus.com/pt/tutorials/the-30-css-selectors-you-must-memorize--net-16048)
>
> Entendendo Flexbox <br />
> [Profile UI | Concept by Ali Sayed - Dribbble](https://dribbble.com/shots/4503860-Profile-UI-Concept?utm_source=Pinterest_Shot&utm_campaign=alisayed&utm_content=Profile%20UI%20%7C%20Concept&utm_medium=Social_Share) <br />
> [Guia Flexbox - Origamid](https://origamid.com/projetos/flexbox-guia-completo/)
>
> Entendendo Grid <br />
> [Guia CSS Grid Layout - Origamid](https://www.origamid.com/projetos/css-grid-layout-guia-completo/)

**Próximo conteúdo**: [Aprofundando no JavaScript]()