Teste de Aptidão para a vaga de Analista de Business Intelligence
===

A Neoway está com uma vaga para Analista de BI para atuar em Floripa.
A equipe de BI da Neoway trabalha na construção de aplicações de Business Intelligence para clientes de maior relevância no mercado nacional e internacional.
São utilizadas as ferramentas de BI (QlikView, Power BI) para a apresentação das views, porém, praticamente todo o processo de ETL é feito com QlikView, ficando alguns jobs a cargo do Pentaho.
Além disto, estamos trabalhando também com o desenvolvimento de soluções utilizando tecnologias web para oferecer dados via APIs e WebApps. Por isso, o candidato que tiver em seus skills o domínio de javascript, nodejs, angular, html5 e css3 terá um plus em seu processo de triagem.

## Observações Gerais

O candidato terá que acessar este repositório, clonar a estrutura do projeto, para então realizar a construção do mesmo em sua máquina local.
Ao término do teste o candidato terá que subir o projeto no github e enviar o link para raphael.pacheco@neoway.com.br

Serão analisados 4 pontos para avaliar a aptidão do candidato a vaga
	- A capacidade do candidato na captura dos dados em disferentes fontes;
	- Manipulação dos dados;
	- Percepção de qual o melhor tipo de modelagem para o problema proposto;
	- Criação de painéis;
		- Qlikview;
		- Power BI;

## Estrutura do projeto

teste_bi
	├───app
	│   ├───pbi
	│   └───qlik
	├───config
	├───files
	│   ├───dataMirrors
	│   ├───dataTransformed
	│   ├───images
	│   ├───spreadsheets
	│   └───storage_pbi
	└───loads
	    ├───dataCloud
	    ├───extract
	    └───transform

**loads**

Pasta para a criação dos arquivos de carga do projeto. Nela temos as pastas:
	- extract -> para extração dos .csv da pasta teste_bi\files\spreadsheets\;
	- transform -> para a criação de possíveis transformadores de dados (ex: CNAE);
	- dataCloud -> criação da nuvem de dados de todas as dimensões, fatos, ou linktables que sejam criadas.

**files**

Pasta para servir como repositório dos stores que serão dados nos scripts criados em loads. Nela temos as pastas:
	- dataMirrors -> receberá os stores de extract;
	- dataTRansformed -> receberá os stores de transform;
	- images -> receberá possíveis imagens que o candidato deseje utilizar em suas views;
	- spreadsheets -> possuí as bases que disponibilizamos para o teste;
	- storage_pbi -> receberá os stores que virão do(os) dataClouds criados.
	
**config**

Pasta que possuí uma config que disponibilizamos para facilitar o trabalho do candidato ;)

**app**

Pasta onde teremos as aplicações (analises) em Qlik e Power BI

## Sobre o Teste

Neste repositório montamos uma estrutura bem parecida a que trabalhamos em nossos projetos.
Disponibilizamos algumas bases de dados (em formato .csv) para que o candidato possam realizar o seu trabalho de análise dos dados neles contidos e em seguida traçar uma estratégia de modelagem e apresentação. Estas bases estao em teste_bi\files\spreadsheets\
Nesta pasta temos uma base de dados cadastrais de 10.000 empresas, dados de lat e long, qtd veículos, flags, setores, ramos de atividade, CNAES, etc.
	- O candidato terá que pegar os arquivo empresas.csv e fazer um dump deste arquivo em um banco de dados relacional. O intuito disto é verificar a extração (ODBC) da base através deste tipo de fonte de dados. Este procedimento é requisito obrigatório para o teste;
	- O candidato terá que pegar os arquivo Setores e Ramos de Atividade.csv e importar para uma collection no mongoDB, para após isto realizar a extração. Este procedimento não é requisito obrigatório, porém caso o candidato opte em não importar os dados para o mongo, pelo menos ele terá que realizar a extração do arquivo .csv diretamente com o Qlik.
	- O arquivo empresasCalc poderá ser carregado diretamente;
	- O arquivo CNAE apresenta 3 campos multivalorados. Devido a isto, o candidato deverá realizar o tratamento destes campos, fazendo com que estes campos deixem de ser multivalorados.

Para a View, precisamos das seguintes análises:
	- Total Geral de empresas;
	- Total de empresas matrizes;
	- Total de empresas filiais;
	- Total de empresas optantes pelo simples e simei;
	- Total de empresas públicas;
	- Total de empresas privadas;
	- Total de empresas ativas;
	- Total de empresas baixadas;
	- Total de empresas mistas;
	- Empresas por UF -> Município (Drilldown);
	- Empresas em um gráfico de mapa;
	- Empresas por faixa de veículos (leves + pesados) -> 0 a 5, 6 a 10, 11 a 15, 16 a 30, 31 a 50, > 50;
	- Filtro de empresas com veículos registrados na antt;
	- Filtro de empresas optantes pelo simples (sim e não);
	- Filtro de empresas optantes pelo simei (sim e não);
	- Empresas por nível e atividade;
	- Empresas por data de abertura;
	- Empresas por Ramos de Atividade (do arquivo Setores e Ramos de Atividade);
	- Empresas por CNAE Principal (tabela, onde CNAE principal tem número de ordem = 0)
	
## Observações
	
	- É recomendada a utilização do Qlik para toda a etapa de ETL, onde os scripts são salvos em arquivos com a extensão .qvs e nos qvws é aplicado o include destes scripts;
	- Uma dica para a view em Qlik é dar um binary no arquivo criado na pasta dataCloud;
	- Este mesmo arquivo que será criado em dataCloud poderá realizar os stores das dims, fatos ou linktables em storage_pbi, onde o Power BI consumirá os dados de lá;
	- Para que fosse possível subir toda a estrutura de diretórios no Git, foi necessário criar um arquivo file.txt. Pedimos por gentileza que ignorem ou excluam estes arquivos ;)