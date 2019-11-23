**Conteúdo anterior**: [**Aprofundando conceitos básicos**](./Aprofundando.md)

# Aprofundando no HTML

### HTML5 e tags semânticas
Depois que a web parou de usar tabelas e entrou na era Tableless, começou a ser usado muito o elemento <code>div</code> para estruturar as páginas. No entanto, atualmente, no HTML5, surgiram tags mais semânticas para priorizar conteúdos de maior relevância e melhorar o SEO¹.
> ¹ Search Optimization Engine

Para melhorar o entendimento: Todo conteúdo dentro do elemento <code>body</code> é parte de uma seção. As seções em HTML5 podem ser aninhadas com base na seção principal definida no elemento <code>body</code>. As novas tags semânticas são <code>section</code>, <code>article</code>, <code>aside</code>, <code>header</code>, <code>footer</code> e <code>nav</code>.

#### Como funciona
O HTML funciona como se fosse um jornal, onde você tem o título principal, os subtítulos e o conteúdo dentro deles. Ou seja, a estrutura fica assim:
```text
1. Título
    1.1 Subtítulo
        | Conteúdo
    1.2 Outro subtítulo
        | Outro conteúdo
2. Outro título
```

E a forma que usávamos com <code>div</code>, seria a seguinte:
```html
<body>
    <div>
        <h1>Título</h1>
        <div>
            <h2>Subtítulo</h2>
            <p>Conteúdo</p>
        </div>
        <div>
            <h2>Outro subtítulo</h2>
            <p>Outro conteúdo</p>
        </div>
    </div>
    <div>
        <h1>Outro título</h1>
    </div>
</body>
```

E a atual com HTML5 e suas tags, seria:
```html
<body>
    <section>
        <h1>Título</h1>
        <section>
            <h2>Subtítulo</h2>
            <p>Conteúdo</p>
        </section>
        <section>
            <h2>Outro subtítulo</h2>
            <p>Outro conteúdo</p>
        </section>
    </section>
    <section>
        <h1>Outro título</h1>
    </section>
</body>
```

O HTML em si, não tem muito segredo, e muito dificilmente você não vai encontrar uma tag específica para um conteúdo que você for colocar.

> **Referências:** <br />
>
> HTML5 e tags semânticas <br />
> [Seções e estrutura de um documento HTML5 - MDN web docs
](https://developer.mozilla.org/pt-BR/docs/Sections_and_Outlines_of_an_HTML5_document)

**Próximo conteúdo**: [Aprofundando no CSS]()