# PostGIS

![](Imagem/Imagem1.png)

Parte teórica da Apresentação do PostGIS

## Pré-requesitos

O que você precisa ter instalado:

```
PostgreSQL
```

## Passo 1 - Instalação

Com a instalação do PostgreSQL executada, o proximo passo é Instalar o PostGIS.

![](Imagem/stack%20builder.png)

Primeiro você procura a aplicação **Application Stack Builder**  

![](Imagem/stack%20builder%202.png)

Após isso você seleciona a versão do PostgreSQL que você usará.

![](Imagem/stack%20builder%203.png)

Logo depois, você vai e seleciona a aplicação PostGIS.

![](Imagem/stack%20builder%204.png)

Agora você seleciona a pasta onde a aplicação será armazenada.

![](Imagem/stack%20builder%205.png)

Para fazer a instalação, você desmarca a caixinha, e da NEXT.

![](Imagem/stack%20builder%208.png)

Depois, é só da NEXT em todas as caixas que aparecer.

## Vinculando a extensão PostGIS à um Banco de Dados

![](Imagem/PgAdmin.png)

Executando o PgAdmin e selecionando o banco de dados que você quer instalar o PostGIS, você executa ferramenta de consulta.

![](Imagem/Create%20Extension.png)

Para instalar a extension no Banco de dados, você executa o comando:

```
CREATE EXTENSION postgis;
CREATE EXTENSION postgis_topology;
```
