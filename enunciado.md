# Robótica Computacional 2021.1

[Mais orientações no README](./README.md)

## Prova P2 AF

**Você deve escolher somente 2 questões para fazer.**


Nome:_______________


Questões que fez:____________


Observações de avaliações nesta disciplina:

* Não fique em um canal/mesa do Teams. Trabalhe sozinho
* Inicie a prova no Blackboard para a ferramenta de Proctoring iniciar. Só finalize o Blackboard quando enviar a prova via Github classroom
* Só é necessário enviar a prova via Github Classroom uma vez
* Caso haja alguma falha ou queda de conexão avise ao professor e reabra o Proctoring. 
* Durante esta prova vamos registrar via Proctoring somente a tela, não a câmera nem microfone
* Ponha o nome no enunciado da prova
* Tenha os repositórios https://github.com/Insper/robot21.1/ ,  https://github.com/arnaldojr/my_simulation e https://github.com/arnaldojr/mybot_description.git  atualizados em seu `catkin_ws/src` .
* Você pode consultar a internet ou qualquer material, mas não pode se comunicar com pessoas ou colegas a respeito da prova
* Todos os códigos fornecidos estão executando perfeitamente. Foram testados no SSD da disciplina na versão 2021.1
* Teste sempre seu código enquanto desenvolver
* Entregue código que executa
* Faça commits e pushes frequentes no seu repositório (tem dicas [no final deste arquivo](./inst
rucoes_setup.md))
* Esteja com o Teams aberto e pronto para receber calls do professor e da equipe. 
* Avisos importantes serão dados no chat da prova no Teams, será feito o tag para a equipe toda para que você não precise ficar na ligação
* Permite-se consultar qualquer material online ou próprio. Não se pode compartilhar informações com colegas durante a prova
* A responsabilidade por ter o *setup* funcionando é de cada estudante
* Questões de esclarecimento geral podem ser perguntadas no chat do Teams
* Se você estiver em casa pode fazer pausas e falar com seus familiares, mas não pode receber ajuda na prova.
* É proibido colaborar ou pedir ajuda a colegas ou qualquer pessoa que conheça os assuntos avaliados nesta prova.
* Os exercícios admitem diversas estratégias de resolução. A prova de cada aluno é única



Existe algumas dicas de referência rápida de setup [instrucoes_setup.md](instrucoes_setup.md)

**Integridade Intelectual**

Se você tiver alguma evidência de cola ou fraude cometida nesta prova, [use este serviço de e-mail anônimo](https://www.guerrillamail.com/pt/compose)  para informar ao professor.  Ou [este formulário](https://forms.gle/JPhqjPmuKAHxmvwZ9)

## Planilha de atendimento

Avise aqui se tiver problemas e ligamos para você. *Não* vamos dar manutenção básica nem explicar teoria hoje.   [https://docs.google.com/spreadsheets/d/13smFYtV2zI6kDAgRCNTJkAR-EWRTsTvKK0aTxoa31BE/edit?usp=sharing](https://docs.google.com/spreadsheets/d/13smFYtV2zI6kDAgRCNTJkAR-EWRTsTvKK0aTxoa31BE/edit?usp=sharing)


## Tabela para questões 1,2 e 3

Verifique neste link quais objetos deve conseguir [https://alinsperedu-my.sharepoint.com/:x:/g/personal/fabio_miranda_al_insper_edu_br/EbV_wvETw9lFg2LBLi1o3u4BzYlQYoQ4hAhg8IuJkRZ75w?e=0sObQT](https://alinsperedu-my.sharepoint.com/:x:/g/personal/fabio_miranda_al_insper_edu_br/EbV_wvETw9lFg2LBLi1o3u4BzYlQYoQ4hAhg8IuJkRZ75w?e=0sObQT)



## Aviso para questões de ROS

**Atenção: ** 

Para fazer estra questão você precisa ter o `my_simulation` e o `mybot_description` atualizado.

    cd ~/catkin_ws/src
    cd my_simulation
    git stash
    git pull

Ou então se ainda não tiver:

    cd ~/catkin_ws/src
    git clone https://github.com/arnaldojr/my_simulation.git

Para o mybot_description:

    cd ~/catkin_ws/src
    cd mybot_description
    git stash
    git pull

Ou então se ainda não tiver:

    cd ~/catkin_ws/src
    git clone https://github.com/arnaldojr/mybot_description



Em seguida faça o [catkin_make](./instrucoes_setup.md). 

## Questão 1 (5.00 pontos)

<img src="./img/Slide1.PNG" width=75%></img>


Seu robô está no cenário visível abaixo:


    roslaunch my_simulation retangulos.launch



#### O que é para fazer

Inicialmente fazer o robô seguir  pista amarela

Depois de uma volta inteira na pista amarela, assim que ver o bicho de interesse, deve passar a seguir a pista alternativa




#### Detalhes de como rodar


O código para este exercício está em: `p1_211/scripts/Q1.py`


**Você vai precisar copiar os arquivos da mobilenet para a pasta p2_21/scripts. Tem eles na Robot211**

Depois:

    rosrun p2_21 Q1.py



|Resultado| Conceito| 
|---|---|
| Não executa | 0 |
| Segmenta o amarelo | 1 |
| Segue a linha amarela | 2 |
| De alguma forma sabe que deu uma volta (veja abaixo)| 3.0 |
| Reconhece o animal de interesse e dá output claro | 4.0 |
| Passa a seguir a nov apista | 5.0 |


*** Saber que deu uma volta  pode ser por tempo ou por ver 
um animal mais de uma vez, ou por odometria. Para contar com uma volta o robô precisa pelo menos voltar à lateral amarela do quadrado que tem o cachorro. 

Casos intermediários ou omissos da rubrica serão decididos pelo professor.



## Questão 2  (3.33 pontos)

Você precisa desenvolver um programa que identifica cruzes brancas, cruzes negras e um combo de interesse dentro de uma região de interesse. 

Você deve ainda devolver uma imagem BGR com seus combos de interesse pintados de vermelho, quando estiverme na região de interesse


Os combos de interesse são sequências de cruzes brancas grudadas horizontalmente em cruzes negras ou vice-versa

Todas as cruzes têm x3.


**Seu combo de interesse e seu tom de cinza se encontram na planilha acima**

![](./q2/cruz50.png)

Esta é uma cruz negra

![](./q2/cantos50.png)

A imagem cruz_branca_negra_simples.png tem cruzes brancas e negras sempre numa sequência branca-negra depois negra-branca

<img width=50% src=./q2/exemplo_quadrante_75_100_125_150.png></img>

A imagem que tem sequências de cruzes brancas e negras e negras e brancas

<img width=50% src=./q2/cruz_branca_negra_simples.png></img>

O programa já chama as imagens de testes. 




#### Orientações

Trabalhe no arquivo `q2/q2.py`. Este exercício **não precisa** de ROS. Portanto pode ser feito até em Mac ou Windows


**Note que tem várias imagens mais simples para testes e um notebook para rascunho na pasta**

|Resultado| Conceito| 
|---|---|
| Não executa | zero |
|Devolve lista com posições i j das cruzes brancas | 1.5|
|Devolve lista com posições i j das cruzes negras | 2.0|
|Devolve seu combo de interesse em qualquer lugar, com imagem pintada | 3.5|
|Devolve seu combo de interesse só na sua regiãpo de cinza, com imagem pintada | 3.5|



## Questão 3 (5.00 pontos)

<img src="./img/Slide3.PNG" width=75%></img>


Seu robô está no cenário visível abaixo:


    roslaunch my_simulation mesa.launch



#### O que é para fazer

Sortear um ângulo entre 0 e 360 graus 

Fazer o robô dar um giro correspondente ao ângulo em malha aberta

Localizar seu cilindro de interesse visualmente

Aproximar-se lentamente usando o laser

Quando o robô estiver a 16 cm do cilindro, tentar pegá-lo (se der uma pancada vale)


Note que as funções do ROS que convertem para ângulo retornam sempre o ângulo de menor magnitude. Isso significa que ângulos maiores que $180^o$ retornarão negativos e será necessário somar $360^o$ ou $2\pi$ para que a magnitude se torne positiva. 

**Execute o controlador do braço com mybot control**

#### Detalhes de como rodar


O código para este exercício está em: `p2_21/scripts/Q3.py`

Para rodar, recomendamos que faça:

    roslaunch my_simulation mesa.launch

Depois:

    rosrun p2_21 Q3.py



|Resultado| Conceito| 
|---|---|
| Não executa | 0 |
| Faz o robo dar um giro aleatório | 0.5 |
| Localiza o cilindro de sua cor e se aproxima visualmente| 1.5 |
| Chega a 16 cm usando o laser| 2.5 |
| Usa a garra para bater no cilindro | 3.0 |
| Faz os ajustes necessarios para pegar o cilindro | 5.0 |


