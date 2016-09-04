---
layout: post
title:  "Inicio da Modelagem do Personagem"
date:   2016-09-04
categories: [maya, personagem]
excerpt_separator: <!--exc-->
img: 2016-09-04-modelagem-personagem/img10.png
autor: Marcelo da Silva
---

A primeira coisa que você precisa ao criar um objeto 3D, é o Concept dele. Para o estilo de jogo que estamos projetando, escolhemos uma imagem da internet de um corpo com uma proporção próxima da que desejamos para a nossa personagem principal. Essa imagem servirá de concept para o nosso modelo. A imagem que foi escolhida foi a seguinte:

<center><img src="/static/img/2016-09-04-modelagem-personagem/img1.jpg"></center>

O que faremos a seguir é colocar essa imagem em um plano no programa Autodesk Maya. Para fazermos isso, precisamos criar um plano no programa, que deverá ter o tamanho proporcional à imagem do seu concept. Nas propriedades da imagem que usaremos de base para o nosso modelo, temos a informação de que seu tamanho é 1113x720. Portanto, para que não tenhamos problema com distorções, colocaremos essa imagem em um plano com essas mesmas medidas.

<center><img src="/static/img/2016-09-04-modelagem-personagem/img2.png"></center>

A seguir, nós criamos uma base para ser o tronco do nosso modelo, um cubo simples serve para começar. Sabemos que o nosso modelo inicial é um cubo, e precisamos transformá-lo em um corpo humano, então sabemos que temos um certo trabalho pela frente. Basicamente, o que temos que fazer é alterar o cubo, adicionando divisões, alterando tamanhos, adicionando arestas e vértices para torná-lo o mais parecido possível com o nosso concept.

Algo que irá nos ajudar nessa tarefa são as 'Orthographic Views' telas que não podem ser rotacionadas e que nos ajudarão a deixar o nosso modelo com o formato de um corpo humano. As principais telas que usaremos são a frontal e a lateral. Também podemos trabalhar com várias janelas ao mesmo tempo.

<center><img src="/static/img/2016-09-04-modelagem-personagem/img3.png"></center>

Uma estratégia importante, que é muito comum se usar quando estamos modelando um objeto simétrico, é modelar apenas metade do objeto e no final da modelagem, copiar a parte modelada para o outro lado. Para isso, é interessante posicionar o nosso concept de uma maneira que torne isso mais fácil, colocando o eixo y no centro da imagem.

<center><img src="/static/img/2016-09-04-modelagem-personagem/img4.png"></center>

Para reproduzir o tronco da imagem em um modelo 3D, as principais ferramentas utilizadas foram as seguintes:

Move Tool (que pode ser acessada no menu do lado esquerdo, ou com a tecla 'W'), sua função é simplesmente mover o objeto selecionado. Se unida com as formas de seleção adequadas, ela se torna muito útil e te traz bons resultados. Para alterar entre a seleção de objetos, faces, arestas ou vértices, é só segurar o botão direito do mouse sobre o seu modelo, que aparecerá um menu com todas as formas de seleção e algumas ferramentas;

<center><img src="/static/img/2016-09-04-modelagem-personagem/img5.png"></center>

Insert Egde Loop Tool (que pode ser acessada na aba 'Mesh Tools'), sua função é criar uma volta (um loop) de arestar no objeto que temos. O uso dessa ferramenta cria mais uma divisão no nosso modelo, e podemos utilizar essa nova divisão para fazer o tronco ficar mais parecido com a personagem. Quanto mais curvado for a parte do corpo que se deseja fazer, mais divisões deverão ser feitas, para que essa parte do corpo modelado não possua arestas rígidas nem cantos;

<center><img src="/static/img/2016-09-04-modelagem-personagem/img6.png"></center>

Extrude (que pode ser acessado na aba 'Edit Mesh' > Components), sua função é criar uma seção a partir das faces selecionadas, que pode ser movimentada para dentro do seu modelo ou para fora. A diferença dessa ferramenta para apenas mover a face é que o extrude diplica a face escolhida e cria novas faces que vão ligar a posição original da face que você está alterando na nova face criada, que poderá ser movida sem alterar a posição e formato da face original.

<center><img src="/static/img/2016-09-04-modelagem-personagem/img7.png"></center>

Para tornar um simples cubo no corpo da personagem, foram colocadas mais divisões onde o tronco possuía mais curvas, e as faces do cubo, agora com mais divisões, foram alterados de maneira a ficar com o formato do corpo. Para isso usamos a movimentação de arestas e, principalmente, de vértices. Movimentamos os vértices de maneira que fiquem sobre o desenho do nosso concept.

<center><img src="/static/img/2016-09-04-modelagem-personagem/img8.png"></center>

Para fazer os braços e pernas da nossa personagem, seguimos a mesma regra. Para isso, continuamos com as mesmas ferramentas e a mesma técnica, e após bastante trabalho, temos o braço utilizando as mesmas técnicas que usamos para fazer o tronco. Para a perna, foi usado uma técnica diferente, pois o formato dela é praticamente cilíndrico até o calcanhar, e além disso, por estar na posição vertical, temos uma facilidade maior de utilizar as ferramentas 'Move Tool' e 'Scale Tool'.

Para fazer a perna do modelo 3D, iniciamos da parte superior da coxa e movemos os vértices para que ficassem no formato de uma seção da perna (um corte quase circular, se visto de baixo). A partir daí, essa seção, com essas proporções foram movidas até o joelho. Para que o formato ficasse o mais próximo possível do concept, foi alterada a posição de todos os vértices de um loop fazendo com que o vértice do extremo ficasse exatamente sobre sua posição no concept. Após isso, alteramos a posição do pivot para que ele ficasse também sobre o extremo do concept. Então foi utilizada a 'Scale Tool' para fazer o outro extremo do modelo ficar sobre o concept, no local correto. Esse processo foi repetido para todas as seções da perna e tanto para a posiçõa frontal do desenho quanto para a posição lateral do desenho.

<center><img src="/static/img/2016-09-04-modelagem-personagem/img9.png"></center>

Para finalizar a parte inicial do corpo, utilizamos a ferramenta 'Mirror Geometry' para copiar a metade produzida do corpo para o outro lado, e obtivemos o resultado a seguir.

<center><img src="/static/img/2016-09-04-modelagem-personagem/img10.png"></center>
<center><img src="/static/img/2016-09-04-modelagem-personagem/img11.png"></center>