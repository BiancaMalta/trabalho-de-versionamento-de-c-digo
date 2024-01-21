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
- Encontre o hash do commit que alterou a cor para amarelo
- Inclua no bisect e criei uma versão principal
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
##### Inicie a busca pelo hash do commit amarelo
```
git bisect start
git bisect bad
git log
```
##### Inclua o hash encontrado no bisect
![incluindo o hash do commit amarelo](https://github.com/BiancaMalta/BiancaMalta-Classe1127/blob/BiancaMalta/Imagem4.png)
##### Como visto na imagem, a partir da alteração do body, o html saiu da versão desejada (first bad commit). Para criar uma versão principal antes disso, utilize o cherry-pick
```
git bisect reset
git checkout main
git cherry-pick hash do commit amarelo
git commit -am 'cherry-pick: versão principal'
```
##### Na main, altere a cor para lilás 
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
##### E para concluir, antes de tirar do local, é necessário configurar os apontamentos, para que o push não vá ao repositório da professora
```
git remote -v
git remote remove origin
git remote add origin https://github.com/BiancaMalta/bianca-malta-classe1127/tree/main
git push origin --all
```
