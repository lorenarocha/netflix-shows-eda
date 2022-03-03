# <font size=8 color=red>Análise Exploratória de shows da Netflix</font>

<div align="justify">

<img src='https://s2.glbimg.com/lz2UNzE6rBXfntWtECDE9bb-6Ic=/smart/e.glbimg.com/og/ed/f/original/2021/01/26/netflix.jpg'>

Com o intuito de aprender as técnicas da análise exploratória e também visualização de dados no `Python`, esse projeto é objeto de estudo para a carreira de <i>Data Analytics</i>. O primeiro passo para a prática é a escolha dos dados, que nesse caso, é o <i>dataset</i> de shows da Netflix, um serviço de <i>streaming</i> conhecido mundialmentem que possui mais de 220 milhões de assinantes. Dessa forma, faz-se importante analisar o que está em seu catálogo e o que os assinantes tem recebido pelo serviço.

# Descrição dos dados

O <i>dataset</i> utilizado pode ser encontrado na plataforma [Kaggle](https://www.kaggle.com/shivamb/netflix-shows), que possui uma variedade de dados para fins de estudo e competição na área de <i>Data Science</i>. O arquivo `netflix_titles.csv` possui 8807 linhas e sua última atualização foi feita em 27/09/2021.

<center>

|Feature|Type|Description|
|---|---|---|
|show_id|object|Identificador único do show|
|type|object|Tipo (Filme ou série)|
|title|object|Título do show|
|director|object|Diretor(es) do show|
|cast|object|Elenco do show|
|country|object|País em que o show foi produzido|
|date_added|object|Data em que o show foi adicionado no catálogo| 
|release_year|int64|Ano em que o show foi lançado| 
|rating|object|Classificação etária| 
|duration|object|Duração total (minutos ou número de temporadas)| 
|listed_in|object|Gêneros que os títulos estão listados| 
|description|object|Sinopse do título| 

</center>

# Execução

Toda a análise foi feita no <b>Jupyter Notebook</b> e pode ser encontrada em `eda-netflix-shows.ipynb`. Então, partindo de processos como:
- download do <i>dataset</i> através do pacote [opendatasets](https://github.com/JovianML/opendatasets)
- importação dos pacotes utilizados
- leitura do arquivo pela biblioteca [pandas](https://pandas.pydata.org)
- estatísticas básicas do <i>dataset</i>, mesmo que em sua maioria sejam variáveis qualitativas
- observação do número de dados faltantes nas colunas `director`, `cast`, `country`, `date_added`, `rating` e `duration`
- preenchimento dos dados faltantes nas colunas  `director`, `cast`, `country`, `date_added` e `rating` com a string `Unavailable`
- na coluna `rating` haviam três linhas com a duração em seu lugar, enquanto que `duration` estava com `NaN`, utilizando a função `loc` foi possível fazer essa alteração
- criação de um dicionário com a classificação dos shows

Após todo o tratamento do <i>dataset</i>, foi possível elaborar a visualização dos dados pelos pacotes [matplotlib](https://matplotlib.org), [seaborn](https://seaborn.pydata.org) e [squarify](https://github.com/laserson/squarify), a fim de responder algumas perguntas.

> <b>Observação:</b> De primeira, pensei como `country` é uma variável qualitativa, então para preencher os dados faltantes dessa coluna, a melhor opção seria colocar a moda do <i>dataset</i> que seria `United States`, porém evidenciaria uma análise tendenciosa. Então, optei por subtituir o `NaN` por `Unavailable`.

# Análise

## Qual é a diferença da quantidade de filme e séries no catálogo?

<img src="netflix-shows\shows-frequency.png">

## Ano de lançamento de filmes e séries

<img src="netflix-shows\release-year-boxplot.png">

## Quais são os 10 países que mais produzem conteúdo?

<img src="netflix-shows\country-top10.png">

## Como tem sido as durações dos shows?

<img src="netflix-shows\duration.png">

## Em qual ano o volume de shows adicionados no catálogo foi maior?

<img src="netflix-shows\releases-per-year.png">

## Qual gênero é o mais frequente?

<img src="netflix-shows\genres-treemap.png">

## Quais são os diretores com mais títulos no catálogo?

<img src="netflix-shows\director-top10.png">

## Atores com maior participação em países como USA e Coreia do Sul

<img src="netflix-shows\cast-usa.png">

<img src="netflix-shows\cast-sk.png">

## Recomendações

#