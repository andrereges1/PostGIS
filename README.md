# PostGIS

![](Imagem/Imagem1.png)

Parte teórica da Apresentação do PostGIS

## Pré-requesitos

O que você precisa ter instalado:

```
PostgreSQL
```

## Instalação do PostGIS

Após concluir a instalação do PostgreSQL, o próximo passo é instalar a extensão PostGIS, que permite trabalhar com dados geoespaciais de forma eficiente.

### Abrindo o Application Stack Builder

Para iniciar a instalação do PostGIS, abra a aplicação **Application Stack Builder**, que geralmente é instalada junto com o PostgreSQL. Este utilitário facilita a instalação de componentes adicionais.

![](Imagem/stack%20builder.png)

### Selecionando a Versão do PostgreSQL

Na interface do **Application Stack Builder**, você será solicitado a selecionar a versão do PostgreSQL que está instalada em seu sistema. Certifique-se de escolher a versão correta para garantir a compatibilidade com o PostGIS.

![](Imagem/stack%20builder%202.png)

### Selecionando a Aplicação PostGIS

Depois de selecionar a versão do PostgreSQL, uma lista de aplicações disponíveis será exibida. Marque a caixa correspondente ao PostGIS e clique em **NEXT** para prosseguir com a instalação.

![](Imagem/stack%20builder%203.png)

### Escolhendo o Diretório de Instalação

Em seguida, você será solicitado a escolher o diretório onde o PostGIS será instalado. É recomendável usar o diretório padrão a menos que você tenha uma razão específica para alterá-lo. Após selecionar o diretório, clique em **NEXT**.

![](Imagem/stack%20builder%204.png)

### Configurando a Instalação

Para avançar na instalação, desmarque a caixa de seleção que pode aparecer e clique em **NEXT**.

![](Imagem/stack%20builder%205.png)

### Finalizando a Instalação

Continue clicando em **NEXT** nas telas subsequentes até que a instalação esteja concluída. O assistente de instalação guiará você por cada etapa, e a instalação do PostGIS pode levar alguns minutos, dependendo da sua máquina.

![](Imagem/stack%20builder%208.png)
<br><br>

## Vinculando a extensão PostGIS a um Banco de Dados

Após a instalação bem-sucedida do PostGIS, o próximo passo é vincular a extensão ao banco de dados em que você deseja trabalhar. Isso permitirá que você utilize as funcionalidades geoespaciais fornecidas pelo PostGIS.

### Abrindo o PgAdmin

Inicie o PgAdmin, a interface gráfica de administração para PostgreSQL. Esta ferramenta facilita a gestão de bancos de dados e é essencial para a vinculação de extensões.

![](Imagem/PgAdmin1.png)

### Selecionando o Banco de Dados

Na árvore de objetos à esquerda, expanda a lista de servidores e localize o banco de dados que você deseja usar com o PostGIS. Clique com o botão direito no nome do banco de dados e selecione `Query Tool` (Ferramenta de Consulta) para abrir um editor de SQL.

![](Imagem/Query.png)

### Executando os Comandos de Instalação da Extensão

No editor de SQL, insira os seguintes comandos para instalar as extensões do PostGIS e do Topology:
```
CREATE EXTENSION postgis;
CREATE EXTENSION postgis_topology;
```
Esses comandos adicionam as funcionalidades geoespaciais ao seu banco de dados, permitindo que você armazene e manipule dados geográficos.

![](Imagem/Create%20Extension.png)

<br>

## Criando uma tabela PONTO com suporte a dados geometry

Com o PostGIS instalado, poderemos finalmente criar uma tabela com suporte a dados **geometry**

### Adicionando Coluna com Suporte a Dados Geoespaciais

Para armazenar dados do tipo `geometry` em uma tabela, é necessário criar uma coluna que ofereça suporte a esse tipo de dado. No exemplo a seguir, criamos uma tabela chamada `ponto` que inclui uma coluna `geom` para armazenar geometrias do tipo `POINT` com o sistema de coordenadas EPSG:4326.

```
CREATE TABLE ponto(
	nome VARCHAR(50),
	geom geometry(POINT, 4326)
);
```

![](Imagem/CREATE%20TABLE.png)

### Inserindo Dados na Tabela

Após a criação da tabela, podemos proceder com a inserção de dados. Para adicionar informações utilizando o formato Well-Known Text (WKT), utilizamos a função `ST_GeomFromText`. Essa função permite converter uma representação de texto de uma geometria em um objeto de geometria que pode ser armazenado na tabela.

```
INSERT INTO ponto (nome, geom) VALUES ('Ponto 1', ST_GeomFromText('POINT(-36.46328362 -8.87669479 )'));
```

![](Imagem/INSERT.png)

### Consultando os Dados na Tabela

Para consultar os dados armazenados na tabela, utilizamos o seguinte comando SQL:

```
SELECT * FROM ponto;
```

Esse comando retorna todos os registros da tabela `ponto`, permitindo que você visualize todas as informações inseridas.

![](Imagem/Saida.png)

### Visualizando o Ponto em um Mapa

Para visualizar os dados em um mapa, clique no ícone ao lado da coluna geom. Essa ação abrirá uma representação geográfica do ponto armazenado, permitindo uma melhor compreensão da sua localização.

![](Imagem/icone.png)

Logo ápos abrirá um mapa com localização dos pontos

![](Imagem/mapa.png)

## Utilizando dados Shapefile no PostGIS

Graças à conformidade com os padrões da OGC (Open Geospatial Consortium), é possível integrar diretamente os dados de um arquivo Shapefile no PostGIS. Isso facilita a inclusão de informações geoespaciais em seu banco de dados, permitindo que você aproveite as funcionalidades avançadas que o PostGIS oferece.

### Modificando a variável de ambiente PATH no Windows

Para configurar o ambiente corretamente, localize a pasta `bin` do PostgreSQL e execute o seguinte comando:

```
set PATH=%PATH%;C:\Program Files\PostgreSQL\<sua_versao>\bin
```

Se a versão do PostgreSQL instalada em sua máquina for diferente da mencionada, certifique-se de substituir `<sua_versao>` pela versão correta que você está utilizando. Isso garantirá que você tenha acesso às ferramentas do PostgreSQL a partir do terminal.

### Convertendo Shapefile em SQL

Para utilizar dados de um arquivo Shapefile em um banco de dados PostgreSQL com a extensão PostGIS, é necessário converter o arquivo Shapefile (.shp) em instruções SQL. Siga os passos abaixo para realizar essa conversão.

#### Passo 1: Preparação do Arquivo Shapefile

1. Download do Arquivo: Certifique-se de que o arquivo Shapefile já esteja baixado em sua máquina. Caso ainda não tenha, você pode obtê-lo no site do IBGE.

2. Organização dos Arquivos: Mova todos os arquivos relacionados ao Shapefile para uma pasta específica. O Shapefile geralmente consiste em vários arquivos com extensões como `.shp`, `.shx`, `.dbf`, entre outros.

#### Passo 2: Acessando o Terminal

Abra o terminal (CMD) do Windows e navegue até a pasta onde os arquivos do Shapefile estão localizados.

#### Passo 3: Executando o Comando de Conversão

Utilize o seguinte comando para converter o arquivo Shapefile em instruções SQL:

```
Shp2pgsql -W <LATIN1> -s 4326 C:\Temp\pernambuco\pernambuco\municipios.shp > municipios.sql
```

Explicação dos Parâmetros:
Shp2pgsql: Este é o utilitário de linha de comando que converte arquivos Shapefile em instruções SQL para serem executadas em um banco de dados PostgreSQL. Ele é parte das ferramentas do PostGIS.

-W LATIN1: A opção -W especifica a codificação de texto a ser utilizada para os dados. A codificação LATIN1 é recomendada para garantir que caracteres especiais sejam corretamente interpretados durante a importação.

-s 4326: A opção -s define o sistema de referência espacial (SRID) dos dados geográficos. O SRID 4326 refere-se ao sistema de coordenadas WGS 84, amplamente utilizado para dados geográficos em longitude e latitude.

C:\Temp\pernambuco\pernambuco\municipios.shp: Este é o caminho completo para o arquivo Shapefile que está sendo convertido. O arquivo municipios.shp contém a geometria e os dados associados dos municípios de Pernambuco.

> municipios.sql: O operador > redireciona a saída do comando para um arquivo. Neste caso, a saída gerada pelo Shp2pgsql (as instruções SQL) será escrita no arquivo municipios.sql, que pode ser utilizado posteriormente para importar os dados no banco de dados PostgreSQL.