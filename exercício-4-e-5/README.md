# Exercício - 4 e 5
### Transfira o repositório do seu grupo para um repositório no seu git e execute o requerido.
#### Nesse exercício foi solicitado:
- Crie uma nova branch 'develop'
- Dentro da nova branch faça os seguintes commits:
  - Commit 1 -> alterar a cor para vermelho
  - Commit 2 -> alterar o título de 'testando as cores' para o seu nome
  - Commit 3 -> alterar a cor para amarelo
  - Commit 4 -> alterar o body
  - Commit 5 -> alterar a cor para rosa
- Supondo que o commit "alterar a cor para amarelo" foi o último correto:
  - Use o bisect para buscar o first bad commit
  - Criei uma versão principal sem o bug
- Na main realize a alteração de cor para lilás
- Volte para o commit anterior
- Faça o merge da develop
- Atualize o no repositório da professora o seu README.md com o link do repositório criado

#### Para isso, foi necessário fazer os seguintes passos:
##### Clonar o repositório especificado e criar a nova branch
```
git clone https://github.com/Herikamachado/grupo2.git
git checkout -b develop
```
##### Na nova branch criada, a cada alteração no index.html, execute o comando abaixo
```
git add .
git commit -m 'mensagem com especificando o que fez'
```
##### Suposição de bug
###### Para longas listas de operações, se torna custoso enontrar a origem do erro. O comando 'bisect' utiliza um algoritmo de pesquisa binária para descobrir qual o commit no histórico do projeto introduziu um "bug". Para utiliza-lo basta informar um commit "bad" (o último da aplicação) e um commit "good" (o que temos certeza que não contém o problema, no caso, o primeiro commit). Então o comando git bisect seleciona um commit entre estes dois pontos extremos e pergunta se o commit selecionado é "bom" ou "ruim". A operação continuará estreitando o intervalo até encontrar o commit exato responsável pela introdução da alteração.
![incluindo o hash do commit amarelo](https://github.com/BiancaMalta/trabalho-versionamento-de-codigo/blob/BiancaMalta/exerc%C3%ADcio-4-e-5/Imagem4.png)
##### Como visto na imagem, a partir da alteração do body, o html saiu da versão desejada (first bad commit). Para criar uma versão principal antes disso, utilize o cherry-pick
```
git bisect reset
git checkout main
git cherry-pick hash do commit amarelo
git commit -am 'cherry-pick: versão principal'
```
##### Na main, altere a cor para lilás 

  <img align="right" src="https://github.com/BiancaMalta/trabalho-versionamento-de-codigo/blob/BiancaMalta/exerc%C3%ADcio-4-e-5/Imagem5.png" width="400" height="550" />
  
```
vi index.html
git add .
git commit -m 'alteração para a cor lilás'
```
##### Volte para o commit anterior e realize o merge da develop
```
git revert HEAD~
git merge develop
git -am "merge branch 'develop'"
```
##### Para concluir, antes de tirar do local, é necessário configurar os apontamentos, para que o push não vá ao repositório da professora
```
git remote -v
git remote remove origin
git remote add origin https://github.com/BiancaMalta/bianca-malta-classe1127/tree/main
git push origin --all
```
##### E como resultado, cheguei ao html da imagem ao lado
### Link do local que efetuei a atividade
[Exercício 4 e 5](https://github.com/BiancaMalta/bianca-malta-classe1127)
