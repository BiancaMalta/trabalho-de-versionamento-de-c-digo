# Exercício - 1
### Trabalhando com commit local
#### Nesse exercício foi solicitado:
- uma branch com o nome do usuário
- um arquivo com o nome dos integrantes
- um arquivo incorreto com formatação txt
- um print do status após o commit do arquivo
- remover o arquivo incorreto
- um prit do status após a remoção

#### Para isso, foi necessário executar os seguintes passos:
##### Clonar o repositório da professora para minha máquina
```
git clone https://github.com/Herikamachado/classe1127.git
```
##### Entrar dentro da pasta para criar uma nova branch e os arquivos requisitados
```
cd classe1127/
git checkout -b BiancaMalta
vi grupo.txt
touch arquivoincorreto.txt
```
##### Adicionar as alterações e comitar
```
git add .
git commit -m 'Criado grupo.txt e arquivoincorreto.txt'
```
##### Ver o status, remover o arquivo incorreto, ver novamente o status e tirar o print solicitado
![Print exigido](https://github.com/Herikamachado/classe1127/blob/BiancaMalta/Imagem2.png)
#### Por último, fazer o commit que resta e subir para o remoto
```
git commit -m 'Remoção do arquivoincorreto.txt'
git push origin BiancaMalta
```
