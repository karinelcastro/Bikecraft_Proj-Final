# Notas!
* Para mudar o endereço do seu diretorio remoto git use:  
```bash
$ git remote set-url origin https://github.com/user/repositorio.git
```

## 20/01/2025
* Quando temos um fundo de qualquer cor que não seja branco e que se espande de ponta a ponta usamos essa cor na tag principal ( `<header>`, por exemplo) e para facilitar a organização do conteúdo e seu posicionamento criamos um container `<div>`.

## 24/01/2025
* Um link para voltar para a home do site não precisa ter "./index.html" já é suficiente usar "./" que significa a "home" do seu site.  
* O `box-sizing: border-box` permite que os valores de `padding` não sejam somados na largura dos elementos, no `max-width` por exemplo.

## 26/01/2025
   ## Dica!
   * Para fazer um efeito interessante em que um sublinhado animado aparece abaixo dos itens de menu em hover, podemos:
   1. criar um pseudo elemento `:after`; 
   2. dar a ele a largura de 100% do elemento pai quando está em hover;
   3. tirar sua exibição usando `width: 0px` quando não está em estado de hover. (no caso o `menu > a` é o pai do after);
   4. dar  a ele display block;
   5. adicionar uma `transition: 0.3s`. 
   * Como seu `content:""` é vazio, usamos o background para dar aparência ao pseudo elemento. 
   * Outro aspecto útil é tirar o elemento after do fluxo do documento, para não ter problemas com padding e posicionamento:
     * (use o `position: absolute` sem se esquecer de usar o `position: relative` no elemento pai).
   ### Assim:
   ```CSS
   .header-menu a{
  display: inline-block;
  color: #fff;
  padding: 16px 0px;
  font-size: 18px;
  position: relative;
  }

  .header-menu a::after{
  content: "";
  display: block;
  height: 2px;
  width: 0px;
  background: #fff;
  margin-top: 4px;
  transition: 0.3s;
  position: absolute;
  }

  .header-menu a:hover::after{
    width: 100%;
  }
   ```

   ### -> Importante!
   * Note que o `:hover` vem antes do `::after` na regra que faz com que ele apenas apareça quando estiver em estado de hover.
   * Para tirar sua visualização em telas menores, use o media querie (`@media(max-width:800px)`, por exemplo) e dentro dele dê ao pseudo elemento o `display: none`.
   * A transição de 3 segundos é necessária para que ele apareça suavemente "crescendo" sob o elemento `a`; 
     * (sem o `transition` ele aparece automaticamente como uma linha sublinhada sem nenhuma animação atraente para o usuário).
---
* Alguns elementos não herdam as características do elemento pai como é o caso da tag `<a>` que não herda, por exemplo a `color` do texto e mantém por padrão os tons de azul (e também roxo para visited);
* Para solucionar isso podemos usar, logo na parte de reset, onde colocamos o `text-decoration: none`, a propriedade `color: inherit`, que significa que o elemento `<a>` sempre vai herdar (inherit) a `color` do pai.
* É importante mater um padrão no código, como, por exemplo colocar o padding sempre de cima para baixo, no caso usar `padding:bottom` no elemento de cima ao invés de usar `padding:top` no segundo elemento.
* Para definir o line-height de um elemento não é recomendado usar um valor fixo, como 72px, pois pode quebrar o layout caso eu diminua o tamanho da fonte, para isso usamos um line-height relativo ao tamanho da fonte.
    * calculamos o tamanho do line-height dividido pelo valor do font-size, assim: 72px/64px = 1.125, então quando diminuirmos a letra o espaçamento da linha continua proporcional ao tamanho da fonte.

## 27/01/2025 - Aula 1005: Introdução 2
* Uma forma de deixar apenas um elemento de outra cor, como o ponto final como é o caso usado no site bikecraft, podemos envolver o "." em um span.
    * outra forma seria com o comando para alterar a ultima letra; (Que eu não me lembro qual é e também não encontrei aqui)

* Box-shadow 
    * box-shadow: eixo x, eixo y, blur (espalhamento), quanto ela cresce além do tamanho do elemento, cor; (por padrão a sombra tem o mesmo tamanho do elemento)

### Aula 1006: Box Shadow
* Para fazer uma imagem "vazar" para fora do container, um alternativa não muito eficiente é usar margem negativa. 
    * Dando uma altura de 100% do elemento pai (container), 
    * usar object-fit: cover para não achatar a imagem, 
    * envolver a imagem numa div para que ela responda melhor ao grid layout, 
        * aí sim damos a ela margem negativa, porém na div e não diretamente na imagem.
* Um problema desse método é que os elementos subsequentes, por ser uma margem negativa, ficam escondidos sob a imagem.

## 28/01/2025 - Aula 1006: Box Shadow
* Uma imagem que pertence a um elemento grid, é recomendado colocar a imagem dentro de uma div, para que ela se comporte melho no layout.
#### Quanto à imagem vazando 
* Podemos solucionar esse problema dando um `box-shadow` ao elemento de bg da seção. No caso, a "introdução-bg" ganha uma sombra branca (da cor do fundo do site).
* _Importante!_
    * Usamos o `box-shadow: inset 0 -120px #fff;`
    * Importante que seja uma sombra interna (inset);
    * Aqui sim colocamos o valor negativo

## 01/02/2025 - Aula 1007: Introdução Responsiva
## _IMPORTANTE!_
Houve uma atualização recente do CSS que não é mencionada no curso: a forma de indicar o `width` no `@media` query. Trocamos isso `@media (max-width: 800px)`
por isso:
`@media(width < 800px)`

### Notas de Aula!
* Podemos usar o media query em qualquer parte do css, não necessariamente no final.
* No caso, vamos criar uma regra de responsividade exclusivamente para o botão `a` com um break point diferente dos demais, portanto, imediatamente após `.introducao a` podemos criar o `@media (max-width: 600px)` e definir os estilos.

## 03/02/2025 - Aula 1008: Tipografia
* Algumas versões de browsers estão bloqueando a importação de fontes via arquivo, por isso é recomendado usar o link, através, por exemplo, do Google Fonts .