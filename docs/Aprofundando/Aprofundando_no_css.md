**Conteúdo anterior**: [**Aprofundando no HTML**](./Aprofundando_no_html.md)

# Aprofundando no CSS

### Índice
+ [CSS e seletores úteis](#CSS-e-seletores-úteis)
+ [Entendendo Flexbox](#Entendendo-Flexbox)
+ [Entendendo Grid](#Entendendo-Grid)

### CSS e seletores úteis
No CSS, você estiliza a estrutura e o conteúdo da sua página, mas para você conseguir estilizar bem, existem alguns seletores que podem ser úteis, e é isso que iremos ver agora.

#### Seletores básicos
Você já deve conhecer os seletores <code>*</code>, <code>.</code>, <code>#</code>, onde cada um representa, respectivamente, <code>all</code>, <code>class</code> e <code>id</code>. 

Vamos testar cada um da seguinte forma, vamos supor que você tenha a seguinte estrutura HTML:
```html
<body>
    <div id="app">
        <h1>Hello World</h1>
        <div class="links">
            <a href="#meulink">Meu Link</a>
            <a href="#meulink2">Meu Link 2</a>
        </div>
        <div class="links">
            <a href="#meulink3">Meu Link 3</a>
            <a href="#meulink4">Meu Link 4</a>
        </div>
    </div>
</body>
```

E a seguinte estrutura CSS:

```css
* { 
    background-color: red;
    color: white;
}
```
> Neste exemplo, toda a sua página terá fundo vermelho e texto branco.

```css
#app * {
    background-color: red;
    color: white;
}
```
> Neste exemplo, apenas os elementos dentro do id app, terão fundo vermelho e texto branco.

```css
.links * {
    background-color: red;
    color: white;
}
```
> Já neste exempo, apenas os elementos dentro da classe links, terão fundo vermelho e texto branco.
>
> Note que a diferença do <code>id</code> para <code>class</code>, é que cada <code>id</code> deve ser único na página, e podemos ter vários elementos com a mesma <code>class</code>.

---


### Entendendo Flexbox
O Flexbox permite fazermos nossos layouts com muito mais facilidade, como por exemplo: colocar elementos um do lado do outro dando um espaçamento entre eles, colocar um de cada lado, ou coisas do tipo.

Você geralmente vai usar 4 propriedades para manipular seus layouts, que serão <code>display: flex</code>, <code>flex-direction</code>, <code>align-items</code> e <code>justify-content</code>.

#### Mas como funciona?
Devemos passar a ver o layout de uma forma diferente, iremos "componentizar" cada parte dele. Veja a imagem a seguir, e em seguida, irei lhe mostrar como fazer o cabeçalho, seguindo o Flexbox.

![Layout - Dribble](https://cdn.dribbble.com/users/594915/screenshots/4503860/dashboard_2.jpg "Profile UI | Concept - Ali Sayed")

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
O Grid nos ajuda a criar layouts mas de uma forma diferente do Flexbox, pode-se dizer que os dois se complementam.

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
> []()

**Próximo conteúdo**: [Aprofundando no JavaScript]()