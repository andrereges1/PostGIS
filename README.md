# PostGIS

![](Imagem/Imagem1.png)

Parte teórica da Apresentação do PostGIS

## Pré-requesitos

O que você precisa ter instalado:

```
PostgreSQL
```

## Passo 1 - Instalação

Com a instalação do PostgreSQL concluída, o próximo passo é instalar o PostGIS.

Primeiro, você procura a aplicação **Application Stack Builder**.  

![](Imagem/stack%20builder.png)

Após isso, você seleciona a versão do PostgreSQL que estará utilizando.

![](Imagem/stack%20builder%202.png)

Em seguida, selecione a aplicação PostGIS.

![](Imagem/stack%20builder%203.png)

Agora, escolha a pasta onde a aplicação será armazenada.

![](Imagem/stack%20builder%204.png)

Para proceder com a instalação, desmarque a caixa de seleção e clique em "NEXT".

![](Imagem/stack%20builder%205.png)

Depois, basta clicar em "NEXT" em todas as caixas que aparecerem.

![](Imagem/stack%20builder%208.png)
<br><br>

## Vinculando a extensão PostGIS a um Banco de Dados

Abra o PgAdmin e selecione o banco de dados no qual deseja instalar o PostGIS. Em seguida, execute a ferramenta de consulta.

![](Imagem/PgAdmin.png)

Para instalar a extensão no banco de dados, execute o seguinte comando:

```
CREATE EXTENSION postgis;
CREATE EXTENSION postgis_topology;
```

![](Imagem/Create%20Extension.png)

<br>

## Criando uma tabela PONTO com suporte a dados geometry

Com o PostGIS instalado, poderemos finalmente criar uma tabela com suporte a dados **geometry**

### Adicionando Coluna com Suporte a Dados Geoespaciais

Para armazenar dados do tipo (`geometry`) em uma tabela, é necessário criar uma coluna que ofereça suporte a esse tipo de dado. No exemplo a seguir, criamos uma tabela chamada (`ponto`) que inclui uma coluna (`geom`) para armazenar geometrias do tipo (`POINT`) com o sistema de coordenadas EPSG:4326.