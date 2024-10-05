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

Na árvore de objetos à esquerda, expanda a lista de servidores e localize o banco de dados que você deseja usar com o PostGIS. Clique com o botão direito no nome do banco de dados e selecione Query Tool (Ferramenta de Consulta) para abrir um editor de SQL.

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