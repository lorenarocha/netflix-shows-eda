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

O serviço de <i>streaming</i> inclui filmes, séries, desenhos, documentários, entre outras coisas. No caso desse <i>dataset</i>, os shows foram condensados em dois tipos, então observa-se que os filmes são maioria, representando cerca de 70% do catálogo, enquanto que <i>TV Shows</i> ficam com os 30% restantes. Apesar de ser apenas uma pequena parcela do catálogo, o número de séries tem aumentado nos últimos anos, incluindo séries produzidas pela própria Netflix, que instaurou essa ideia no mercado. Serviço de <i>streaming</i> que produz conteúdo para a plataforma e hoje, muitos outros serviços também criam filmes e séries.

<img src="netflix-shows\shows-frequency.png">

## Ano de lançamento de filmes e séries

Para a visualização de `release_year`, os dados foram divididos nos dois tipos e tem que o lançamento de série, nos últimos anos, tem crescido em relação à produção de filmes. É importante ressaltar que os <i>outliers</i> dos filmes estão no período de 1942 até 2002, quando essa produção fica mais frequente e 50% dos dados se encontra no período de 2003 a 2016. Já a produção das séries se concentram mais a partir do ano de 2010.

<img src="netflix-shows\release-year-boxplot.png">

## Quais são os 10 países que mais produzem conteúdo?

Era esperado que Estados Unidos e India liderassem o ranking por conta de suas indústrias cinematográficas que são as maiores do mundo: <i>Hollywood e Bollywood</i>, então a Netflix aproveita essa quantidade exarcebada de produções para implementar seu catálogo. Logo após os dois países, o catálogo possui mais produções do Reino Unido, Canadá, França, Japão, entre outras nações que vem ganhando espaço na indústria com seus conteúdos.

<img src="netflix-shows\country-top10.png">

De 2008 a 2011, o catálogo possuía apenas produções dos Estados Unidos, visto que a empresa surgiu como uma plataforma online de locação de DVDs no país e após alguns anos, virou um serviço de <i>streaming</i> utilizado mundialmente. Então, com essa expansão, o catálogo começou a ser globalizado e assim, produções de outros países fariam parte da Netflix. Apesar da Índia ser o segundo país com mais títulos no catálogo, seus shows só começaram a ser adicionados no ano de 2016, com maior volume em 2018, após esse período, o número de produções indianas adicionadas no catálogo diminuiu. Enquanto que produções dos outros países começaram a se destacar a partir de 2015 com o aumento na quantidade de títulos adicionados. Vale lembrar que o <i>dataset</i> não possui o ano de 2021 completo, então não é possível afirmar que houve queda na adição de títulos desses países.

<img src="netflix-shows\country-top10-year-added.png">

## Como tem sido as durações dos shows?

Filmes lançados antigamente possuíam curta duração, mas com o passar dos anos, sua duração foi aumentando chegando a mais de duas horas. Atualmente, a duração está concentrada em filmes menores, denominados curtas e filmes de até 170 minutos. São poucos os que passam desse limite, como exemplo o episódio **Bandersnatch** da premiada série <i>Black Mirror</i> que foi classificado como filme e possui 5 horas por conta da forma interativa em que os telespectadores podem tomar as decisões pelo personagem principal.

Já para as séries de TV, o catálogo conta com mais de 1750 séries que possuem apenas uma temporada e esse número cai bastante com séries que têm duas ou mais temporadas, isso acontece provavelmente porque é mais difícil de manter um contrato de direitos sobre uma obra com várias temporadas, havendo um gasto maior e isso acontece para produções originais também, visto que precisam de um capital maior para ser mantidas. A título de curiosidade, a única série de 17 temporadas no catálogo é **Grey's Anatomy**.

> **Observação:** optou-se por não fazer um gráfico de dispersão dos seriados, pois o <i>dataset</i> considera o ano da última temporada adicionada na plataforma.

<img src="netflix-shows\duration.png">

## Em qual ano o volume de shows adicionados no catálogo foi maior?

Com o início da plataforma, poucos filmes foram adicionados entre os anos de 2008 a 2014 e com sua popularização, a empresa aumentou seu catálogo consideravelmente ao longo dos anos. Porém, com a chegada da pandemia da COVID-19, a produção na indústria cinematográfica diminuiu por conta da quarentena, mas outro motivo possível para essa diminuição no volume de shows adicionados no catálogo é o aparecimento de novas plataformas de <i>streaming</i>, havendo maior competição entre direitos autorais, de títulos que antes teriam maior probabilidade de entrar na Netflix. 

<img src="netflix-shows\releases-per-year.png">

## Qual gênero é o mais frequente?

A visualização de dados pela técnica de <i>treemap</i> é bem importante para dados com muitas categorias, então existe uma divisão desses "ramos" da árvore através de retângulos, sendo seu tamanho e cor proporcionais à dimensão especificada nos dados, nesse caso é a quantidade de títulos em relação ao gênero. Tanto para filmes quanto para séries, os gêneros com mais títutlos são internacionais (essa divisão deve ser feita em relação às produções estadunidenses), dramas e comédias. Gêneros que estão em alta ultimamente, como documentários e séries criminais também estão presentes no catálogo em uma quantidade considerável. Mesmo com o aumento de produções LGBTQIA+ em todo o mundo, existem apenas 102 shows desse gênero no catálogo.

<img src="netflix-shows\genres-treemap.png">

### Outras visualizações foram feitas como os 10 diretores com mais títulos, atores em alta de países como Estados Unidos e Coreia do Sul e podem ser encontradas no diretório `netflix-shows`.


## Recomendações

#

- Atualização do <i>dataset</i> com adição de todo o ano de 2021
- Visualização de dados de bilheteria, orçamento, classificação através de notas de espectadores, utilizando outro conjunto de dados
- Análise de sentimento das descrições dos shows, comparar com o gênero atribuído, observar se existe muita diferença