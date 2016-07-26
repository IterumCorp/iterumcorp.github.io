---
layout: post
title:  "Câmera dinâmica"
date:   2016-07-23
categories: [camera, unreal, blueprint]
excerpt_separator: <!--exc-->
img: 2016-07-23-camera-dinamica/PostIMG.PNG
---

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/XvBQuHH1rfw" frameborder="0" allowfullscreen></iframe></center>

O vídeo acima mostra como ficou o resultado final da câmera, com todas suas possíveis transições. Nesse post vou tentar passar como criar uma câmera dinâmica que pode ser utilizada em três opções diferentes: Personagem andando na vertical, na horizontal, ou no eixo Z.
Pra criar a câmera eu usei como personagem o bonequinho padrão da unreal (peguei do modelo “3rd person”). A câmera em si é feita toda em uma única blueprint e o tipo dela é “Camera Actor”


<center><img src="/static/img/2016-07-23-camera-dinamica/CâmeraActor.PNG"></center>


Dentro da blueprint vamos trabalhar apenas no Event Graph, onde faremos as funções que tornaram a câmera utilizável. A primeira coisa que eu recomendo fazer é criar as funções e variáveis que vamos utilizar, que são as seguintes:


<center><img src="/static/img/2016-07-23-camera-dinamica/Funções1.PNG">
<img src="/static/img/2016-07-23-camera-dinamica/Variaveis.PNG"></center>


A primeira variável é uma referência ao nosso personagem:
 

<center><img src="/static/img/2016-07-23-camera-dinamica/VariavelPersonagem.png"></center> 


Partindo para as execuções em si, temos os eventos que são executados logo quando o jogo é iniciado, sendo eles:


<center><img src="/static/img/2016-07-23-camera-dinamica/BeginPlay.PNG"></center> 


Primeiro pegamos o personagem no index 0 (que é o nosso único personagem na cena) e atribuímos ele a variável que já havíamos criado “Personagem”. Além disso, a função SetVetorDistancia encontra a distância em todos os eixos da câmera até o personagem e volta isso em um vetor:


<center><img src="/static/img/2016-07-23-camera-dinamica/VetorDistancia.PNG"></center>


Com essas duas variáveis iniciais instanciadas podemos começar a trabalhar no funcionamento da câmera. A primeira coisa a se fazer é que a câmera tem que estar sempre olhando para o personagem, então a função AtualizaCamera faz com que a câmera fique sempre olhando para o personagem (atualizando sua rotação):


<center><img src="/static/img/2016-07-23-camera-dinamica/AtualizaCamera.PNG"></center>


OBS.: “Camera Component” é um dos componentes criados junto a blueprint.
Após isso, chamamos a próxima função AtualizaDistancia que encontra a distância entre o personagem e a câmera. Pode parecer um pouco confuso isso agora, visto que já tínhamos uma função que encontrava todas as distancias e as armazenavam em um array. A diferença agora é que essa variável é atualizada todo tick do jogo e é composta por apenas um valor, a distância em linha reta da câmera até o personagem, ficando com a seguinte estrutura:


<center><img src="/static/img/2016-07-23-camera-dinamica/AtualizaDistancia.PNG"></center>


A próxima função a ser chamada é uma função que normaliza essa distância entre 0 e 1 dados os parâmetros das variáveis DistMin e DistMax que já foram criadas. Por exemplo: Se DistMin é 0 e DistMax é 1000, se a Distancia tiver em 500 ela é convertida para 0.5. Além dessa normalização, usamos a função Clamp que faz com que os valores não possam ultrapassar 0 e 1.


<center><img src="/static/img/2016-07-23-camera-dinamica/NormalizaDistancia.PNG"></center>


Agora que temos a atual distancia normalizada, podemos brincar com várias coisas, eu optei por alterar o FOV da câmera conforme a distância do jogador a mesma. Essa função usa as outras duas variáveis, FOVMin e FOVMax, que são os limites do FOV. A função “Lerp” é usada para converter o valor da distancia normalizada:


<center><img src="/static/img/2016-07-23-camera-dinamica/AtualizaFOV.PNG"></center>


Agora chegamos a última função: AtualizaPosicao. Essa é a mais complicada de todas até agora, visto que é ela que movimenta a câmera no eixo que você escolher. A primeira coisa que fazemos é usar um SwitchCase para parametrizar a função e deixar possível sua alteração direto da tela do editor com a variável “Direção”. Essa variável pode tomar 3 valores: “h”, “v” e “z”, que correspondem a horizontal, vertical e o eixo z:


<center><img src="/static/img/2016-07-23-camera-dinamica/AtualizaPosiçãoInicio.PNG"></center>


Alem do switch, recuperamos a posição atual do personagem no mapa. Após isso, seguimos o caminho especificado pela variável Direção, sendo as três possibilidades as seguintes:


<center><img src="/static/img/2016-07-23-camera-dinamica/AtualizaPosiçãoHorizontal.PNG"></center>
<center><img src="/static/img/2016-07-23-camera-dinamica/AtualizaPosiçãoVertical.PNG"></center>
<center><img src="/static/img/2016-07-23-camera-dinamica/AtualizaPosiçãoEixoZ.PNG"></center>


Com essa função concluímos a atual câmera, só falta chamar elas:


<center><img src="/static/img/2016-07-23-camera-dinamica/Funções.PNG"></center> 


Agora podemos colocar uma direto no editor e trabalhar com ela nas transições. Ao colocar uma instancia de câmera no editor, temos acesso diretos as variáveis que podem alterar o visual da câmera, sendo eles:


<center><img src="/static/img/2016-07-23-camera-dinamica/VariaveisNoEditor.PNG"></center>


Podemos então, usar a blueprint do level, por exemplo, para fazer as transições em sí. A função utilizada para isso é a “Set View Target with Blend”:


<center><img src="/static/img/2016-07-23-camera-dinamica/LevelBlueprint.PNG"></center>


Usei um trigger que quando o jogador passa por ele, a câmera se altera para a especificada. Além disso, o evento BeginPlay é chamado para que alguma câmera esteja relacionada com o personagem ao início do jogo.
E com isso terminamos nosso primeiro post no blog! Espero que tenha sido claro e caso alguma dúvida permaneça fique à vontade para usar a seção de comentários abaixo.

Referências utilizadas:
https://www.youtube.com/watch?v=UMcmqsMzcFg
https://www.youtube.com/watch?v=nKM8sBH5Uu4
https://www.youtube.com/watch?v=etk4sqtM7xI
https://www.youtube.com/watch?v=zWMgRDa3bKY&list=PLZlv_N0_O1gaCL2XjKluO7N2Pmmw9pvhE&index=71

