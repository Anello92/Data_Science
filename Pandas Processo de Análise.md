# Pandas: Processo de Análise

Pandas é uma poderosa biblioteca de **análise e manipulação de dados de código aberto**. Ele pode ajudá-lo a fazer várias operações sobre os dados e gerar diferentes relatórios sobre eles. Vou dividir isso em dois artigos...

1. Básico, que eu vou cobrir nesta história. Vou cobrir funções básicas pandas que lhe darão uma visão geral de como você pode começar a trabalhar com Pandas e como ele pode ajudá-lo a economizar muito do seu tempo.
2. Avançado, através de funções avançadas que facilita a resolução de problemas de análise complexos. Abrange temas como estilo, plotagem, tabelas pivôs, etc. 

Até o final d artigo, seremos capazes de responder a seguir:

1. Como ler dados de diferentes formatos.
2. Exploração de dados usando diferentes APIs.
3. Quais são as dimensões de Dados.
4. Como encontrar o Resumo de Dados.
5. Como verificar diferentes estatísticas sobre Dados.
6. Como selecionar o subconjunto de Dados.
7. Um forro para contar valores únicos com frequências de cada valor.
8. Como filtrar os dados com base nas condições.
9. Salvar dados em diferentes formatos.
10. Aplicando várias operações usando encadeamento.

Antes de começar, certifique-se de ter instalado Pandas. Se não, usar o seguinte comando para baixá-lo.

```python
# If you are using Anaconda Distribution (recommended)
conda install -c conda-forge pandas

# install pandas using pip
pip install pandas

# import pandas in notebook or python script
import pandas as pd
```

## **1. Ler dados: read_csv ; read_excel ; read_json**

O ponto de partida de qualquer análise de dados é a aquisição do conjunto de dados. Pandas fornecem diferentes funções para ler os dados de diferentes formatos. Os mais usados são —

## **read_csv()**

Isso permite que você leia um arquivo CSV.

```python
pd.read_csv('path_to_your_csv_file.csv')
```

### Ler arquivos em Pandas

Os pandas fornecem diferentes opções para configurar nomes de colunas ou tipos de dados ou o número de linhas que você gostaria de ler. Confira os Pandas read_csv API para mais detalhes:

[pandas.read_csv - pandas 1.2.0 documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html)

## **read_json()**

Esta API da Pandas ajuda a ler dados JSON e funciona muito bem para dados já achatados. Vamos dar um exemplo JSON para ver como podemos convertê-lo em uma mesa plana.

```python
# Sample Record: Flattend JSON i.e. no nested array or dictionary
json_data = {
    "Scaler": "Standard",
    "family_min_samples_percentage": 5,
    "original_number_of_clusters": 4,
    "eps_value": 0.1,
    "min_samples": 5,
    "number_of_clusters": 9,
    "number_of_noise_samples": 72,
}
# reading JSON data
pd.read_json(json_data)
```

Apenas lendo o JSON converteu-o em uma mesa plana abaixo.

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled.png)

## json_normalize() para dados semiestruturados

Não funciona bem quando os dados JSON são semiestruturados, ou seja, contém lista aninhada ou dicionários. Pandas fornecem uma API **json_normalize** para isso também se você quiser aprender mais, confira:

[How to parse JSON data with Python Pandas?](https://towardsdatascience.com/how-to-parse-json-data-with-python-pandas-f84fbd0b1025)

## Tipos de dados que Pandas suporta

Existem muitos outros tipos de dados que pandas suporta. Verificar a documentação do Pandas quando usarmos outros tipos de dados.

[Input/output - pandas 1.2.0 documentation](https://pandas.pydata.org/pandas-docs/stable/reference/io.html)

Lendo o conjunto de dados do Titanic que vamos usar aqui usando o comando read_csv():

```python
# Loading Titanic Dataset into titanic_data variable
titanic_data = pd.read_csv('titanic_train.csv')
```

Isso criará um DataFrame pandas (como tabelas) e o armazenará na variável titanic_data.

Em seguida, veremos como obter mais detalhes sobre os dados que carregamos.

## 2. Explorar dados

Uma vez que tenhamos carregado os dados, gostaríamos de revisá-los. Pandas fornecem diferentes APIs que podemos usar para explorar dados.

## head**( )**

Isso é como um comando TOP no SQL e nos dá 'n' registros desde o início do DataFrame.

```python
# Selecting top 5 (n=5) records from the DataFrame
titanic_data.head(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%201.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%201.png)

## tail**( )**

Isso nos dá os registros 'n' do final do DataFrame.

```python
# Selecting last 5 (n=5) records from the DataFrame
titanitc_data.tail(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%202.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%202.png)

## sample()

Isso capta aleatoriamente o número 'n' de registros dos dados. Nota: a saída deste comando pode ser diferente em diferentes corridas.

```python
titanic_data.sample(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%203.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%203.png)

## **3. Dimensões de dados usando a forma**

Uma vez que temos os dados, precisamos saber quantas linhas ou colunas estamos lidando:

## shape()

```python
# shape of the dataframe, note there is no parenthesis at the end as it is a property of dataframe
titanic_data.shape
(891, 12)
```

(891, 12) significa que temos 891 linhas e 12 colunas em nosso conjunto de dados titanic.

## **4. Resumo de Dados utilizando info( )**

Vamos ver a saída deste primeiro:

## info()

```
titanic_data.info()
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%204.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%204.png)

Como você pode ver 'info' fornece um bom resumo dos dados que temos, vamos entendê-los um por um.

1. Detalhes do índice- cada dataframe em Pandas tem um índice que, basicamente, se você está familiarizado com SQL, é como um índice que criamos para acessar os dados. Aqui significa que temos um RangeIndex de 0 a 890, ou seja, um total de 891 linhas.
2. Cada linha na tabela gerada por 'info' nos dá os detalhes sobre a coluna que temos, o número de valores que estão lá na coluna e o tipo de dados que os pandas atribuíram. Isso é útil para ter um vislumbre de dados perdidos como podemos dizer que temos dados 'Age' apenas para 714 linhas.
3. Uso da memória- Pandas carrega o quadro de dados na memória e isso nos diz quanta memória nosso conjunto de dados está usando. Isso é útil quando temos grandes conjuntos de dados e, portanto, os pandas têm uma API específica 'memory_usage' para mais opções.

## **5. Estatísticas de dados usando describe( )**

## describe()

Isso nos dá as estatísticas sobre o conjunto de dados. Como você vê para o nosso dataframe abaixo ele mostra:

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%205.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%205.png)

Isso nos dá muitas informações para cada coluna, como contagem de registros (não conta registros ausentes como você pode ver em Age), média, desvio padrão, percentuais mínimos e diferentes quânticos. 

Por padrão, este comando fornece informações sobre tipos de dados numéricos como int ou float. Para obter estatísticas sobre nossas colunas de "objeto", podemos executar... Como você pode ver, isso nos dá muitas informações para cada coluna, como contagem de registros (não conta registros ausentes como você pode ver em Age), média, desvio padrão, percentuais mínimos e diferentes quânticos. 

Por padrão, este comando fornece informações sobre tipos de dados numéricos como int ou float. Para obter estatísticas sobre nossas colunas de "objeto", podemos executar...

### describe(include=['O'])

```python
# show stats about object columns
titanic_data.describe(include=['O'])
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%206.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%206.png)

Adicionamos parâmetro 'incluir' para descrever que é uma lista de objetos, podemos passar vários valores como...

- include = ['O', 'int64'] — dará estatísticas sobre colunas do tipo Object e Int64 no DataFrame.
- include = ['O', 'float64'] — dará estatísticas sobre colunas do tipo Object e float64 no DataFrame.

## **6. Seleção de dados usando loc e iloc**

São funções muito úteis para nos ajudar na seleção de dados. Usando estes, podemos selecionar qualquer parte dos dados. Para entendê-lo melhor, vamos alterar o índice dos dados.

### set_index()

Definindo um índice para o dataset.

```python
# Change index of our DataFrame from RangeIndex to 'Ticket' values
titanic_ticket_index = titanic_data.set_index('Ticket')
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%207.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%207.png)

## **loc( )**

Isso seleciona dados com base nos rótulos, ou seja, nomes das colunas e linhas. Nos dados acima, por exemplo, os rótulos de linha são como A/5 21171, PC17599, 113803, e as etiquetas de coluna são como PassengerId, Survived, Sex. A sintaxe geral para loc:

```python
dataframe_name.loc[row_labels, column_labels]
```

***Selecionando uma única linha.***

Insira o rótulo da linha que você deseja, ou seja, se quisermos selecionar 'Ticket' onde o valor é 'A/5 21171'.

```python
# notice we need to use [] brackets

# This returns the data for the row which matches the name.
titanic_ticket_index.loc['A/5 21171']
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%208.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%208.png)

***Selecionando várias linhas***

Muitas vezes precisamos selecionar várias linhas que gostaríamos de analisar mais adiante. A API .loc pode pegar uma lista de row_labels que você gostaria de selecionar, ou seja.

```python
# we can supply start_label:end_label
# here we are selecting rows from label 'PC 17599' to '373450'
titanic_ticket_index.loc['PC 17599':'373450']
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%209.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%209.png)

Nota- Isso não funcionará se várias linhas tiverem os mesmos rótulos.

***Selecionando coluna única***

É semelhante à maneira como selecionamos as linhas, mas ao selecionar colunas precisamos dizer aos Pandas as linhas que gostaríamos de selecionar. Podemos usar ':' no lugar de row_label o que significa que gostaríamos de selecionar todas as linhas.

```python
# selecting Embarked column for all rows.
titanic_ticket_index.loc[:,'Embarked']
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2010.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2010.png)

***Selecionando várias colunas***

Semelhante ao que fizemos para várias linhas, só precisamos dizer aos Pandas quais linhas estamos selecionando.

```python
# Selecting Sex, Age, Fare, Embarked column for all rows.
titanic_ticket_index.loc[:,['Sex','Age','Fare','Embarked']]
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2011.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2011.png)

ou como:

```python
# we can supply column start_label:end_label
# here we are selecting columns from label 'Sex' to 'Embarked'
titanic_ticket_index.loc[:, 'Sex':'Embarked']
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2012.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2012.png)

***Selecionando linhas e colunas específicas***

Podemos combinar a seleção em linhas e colunas para selecionar linhas e colunas específicas:

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2013.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2013.png)

### iloc()

Isso funciona de forma semelhante ao loc, mas seleciona as linhas e colunas com base no índice em vez dos rótulos. Ao contrário dos rótulos, os índices sempre começam de 0 a number_of_rows-1 para linhas e 0 a number_of_columns-1 para colunas.

```python
# selecting specific rows and columns: example 2
# we can use start_index:end_index for both columns and rows.
# selecting 3rd to 6th row and 1st to 4th column 
# end_index should be 1 greater the row or column number you want
titanic_ticket_index.iloc[3:7, 1:5]
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2014.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2014.png)

## **7. Valores únicos nas colunas utilizando value_counts( )**

## value_counts()

Value_counts nos dá a contagem dos valores únicos em uma coluna que é muito útil para conhecer informações como

- Valores diferentes que você tem na coluna.
- Valor mais frequente.
- a proporção do valor mais frequente.

```python
# value counts for the Sex column.
titanic_data['Sex'].value_counts()
# output
male      577
female    314
Name: Sex, dtype: int64
```

Como você pode ver que nosso conjunto de dados contém mais número de machos. Podemos até normalizá-lo para ver distribuição entre valores.

## value_counts(normalize=True)

```python
# value counts normalized for Sex column
titanic_data['Sex'].value_counts(normalize=True)
#output
male      0.647587
female    0.352413
Name: Sex, dtype: float64
```

Isso significa que a proporção para o sexo masculino: feminino em nosso conjunto de dados é de aproximadamente 65:35.

## **8. Filtrar dados usando consulta( )**

Normalmente, trabalhamos com grandes conjuntos de dados que são difíceis de analisar. A estratégia, nesse caso, é filtrar os dados em diferentes condições e analisá-los. Podemos fazê-lo com apenas uma linha de código usando a API de Consulta pandas.

Vamos dar alguns exemplos para entendê-lo melhor.

***Selecione linhas com Age > 15.***

```python
# first 5 records that has Age > 15
titanic_data.query('Age > 15').head(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2015.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2015.png)

***Selecione machos que sobreviveram.***

```python
# first 5 males who survived
titanic_data.query('Sex=="male" and Survived==1').head(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2016.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2016.png)

Podemos definir variáveis e usá-las para escrever uma consulta de filtro. Seria útil quando precisamos escrever roteiros.

```python
# gender to select and min_fare, these can be passed as part of argument to the Script
gender_to_select = "female"
min_fare = 50
# querying using attribute passed
titanic_data.query('(Sex==@gender_to_select) and (Fare > @min_fare)')
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2017.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2017.png)

## **9. Salvar dados usando to_csv ou to_excel**

Uma vez que temos os dados necessários após a seleção ou filtragem, precisamos salvá-lo para

- Compartilhe com os outros.
- Use-o em outro caderno.
- Visualize-o usando algumas ferramentas.

Como ler dados, o Pandas fornece diferentes opções para salvar os dados. Vou passar por duas APIs principais que são comumente usadas. Você pode consultar a [documentação do Pandas](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html) para outros formatos nos quais você pode salvar os dados.

## **to_csv()**

Isso permite que você economize em um arquivo CSV.

```python
# Save data for males who survived into CSV file
males_survived = titanic_data.query('Sex=="male" and Survived==1')

# Saving to CSV, index=False i.e. do not write Index.
males_survived.to_csv('males_survived.csv', index=False)
```

## **to_excel()**

Isso permite que você economize em um arquivo Excel. Pandas exigem que um pacote **Openpyxl** seja instalado. Se você não tiver, instale-o usando —

```python
# If you are using Anaconda Distribution (recommended)
conda install -c conda-forge openpyxl
# install openpyxl using pip
pip install openpyxl
```

Vamos salvar em um arquivo Excel:

```python
# Save the data for passengers travelling with a Sibling or Parent
passengers_not_alone = titanic_data.query('SibSp==1 | Parch==1')
# Saving to excel, index=False i.e. do not write Index.
passengers_not_alone.to_excel('travelling_with_parent_sibling.xlsx', index=False)
```

## **10. Encadeamento de múltiplas operações**

Antes de terminar, vamos aprender sobre uma das características poderosas dos Pandas, ou seja, o encadeamento. Podemos aplicar várias operações no DataFrame sem salvá-lo em um dataframe temporário (#NamesAreHard) o que torna seu código limpo e fácil de ler. 

```python
# Here we first queried the data and then selected top 5 rows.
titanic_data.query('Sex=="male" and Survived==1').head(5)
```

O código acima é útil nos cenários onde não temos certeza sobre a saída. Ele ajuda a aplicar a operação e verificar diretamente as linhas superiores.

Na última seção, tivemos que primeiro criar um DataFrame temporário (males_survived) para armazenar os dados dos machos que sobreviveram e depois os usamos para salvar em um arquivo CSV. 

Usando o encadeamento, podemos fazer isso em apenas uma linha e até não precisamos fazer uma cópia:

```python
# we used chaining to first filter and then save the records
titanic_data.query('Sex=="male" and Survived==1').to_csv('males_survived.csv', index=False)
```

Podemos praticamente acorrentar qualquer operação em Pandas desde que o resultado da última operação seja uma série ou um dataframe.

---

## Pandas Pt.02

Vou usar dados covid-19 de código aberto fornecidos pelo Our World In Data.

[Coronavirus Source Data](https://ourworldindata.org/coronavirus-source-data)

Neste artigo, estaremos cobrindo com exemplos:

1. Agregação de dados usando groupby() e agg().
2. Plotagem dados usando plot().
3. Estilizar o DataFrame do Pandas usando a propriedade .style.
4. Pivotando os dados, convertendo dados de formato longo em formato amplo.
5. Encontrar linha e coluna com valor mínimo ou máximo usando idxmin() e idxmax().
6. MultiIndex- simplificando suas consultas.
7. Combinando o MultiIndex em um único índice.

Vamos analisar o conjunto de dados em detalhes antes de aplicar as operações.

## **Detalhes do conjunto de dados**

> ***Our world in data*** mantém dados covid-19 que atualizam diariamente. Inclui casos confirmados, número de óbitos e testes relacionados ao Covid-19. Vamos usar dados de 7 de agosto de 2020 e ele contém 35 colunas com várias informações como PIB do país, instalações de lavagem de mãos, etc.

Para fins de demonstração, usaremos um subconjunto de dados contendo:

- iso_code — código alfa 3 para o país.
- continente - continentes do mundo.
- localização — país.
- data — data para os casos relatados.
- new_cases — novos casos notificados na data.
- new_deaths — novas mortes relatadas na data.
- new_tests — novos testes de corona realizados na data.

Além disso, vamos usar os dados do último dia 10 apenas de 29 de julho a 7 de agosto de 2020. 

# **1. Agregação de Dados utilizando groupby e agg( )**

Pandas fornecem diferentes APIs para agregar os dados. Vamos ver como podemos usá-los para executar agregações simples e complexas em uma linha.

## **groupby()**

Suponha que precisamos encontrar o número total de novos casos relatados a cada dia. Podemos fazer isso usando a agregação simples **groupby():**

```python
# here we are chaining multiple operations together
# Step 1: grouping data by date.
# Step 2: selecting new_cases from the group.
# Step 3: calculating the sum of the new_cases.
# Step 4: doing a groupby changes the index, so resetting it
# Step 5: selecting Last 5 records.
data.groupby('date').new_cases.sum().reset_index().tail(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2018.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2018.png)

## **Agregando múltiplos campos**

No exemplo acima, nós apenas agregamos um campo, ou seja, 'new_cases'. E se precisarmos de múltiplas agregações para um grupo? Podemos combinar groupby() com agg() nesse caso. Vamos dizer, precisamos encontrar -

- o número total de casos notificados a cada dia.
- o número máximo de casos notificados por um país para cada dia.
- o número total de óbitos notificados a cada dia.
- o número máximo de mortes relatadas por um país.
- o número total de testes realizados a cada dia
- o número total de países relatando dados por um dia.

Tudo isso pode ser feito com apenas uma linha de código, resultando em um índice **MultiColumn:**

```python
# we are finding totals using sum and maximum using max
# Also, we used nunique to find unique number of countries reporting

data.groupby('date').agg({'new_cases':['sum','max'], 
                          'new_deaths':['sum','max'],
                          'new_tests':['sum'],
                          'location':'nunique',
                         }).reset_index().tail(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2019.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2019.png)

## Nomeando agregações

Se você notou a saída acima, ela nos deu os resultados, mas os nomes das colunas não são amigáveis, pois está apenas usando nomes de coluna existentes. Podemos usar pandas para nomear cada agregação na saída. 

Para o mesmo problema acima, podemos fazer:

```python
# naming the aggregations, you can use any name for the aggregate
filtered_data.groupby('date').agg(
               total_new_cases = ('new_cases','sum'),
               max_new_cases_country = ('new_cases','max'),
               total_new_deaths = ('new_deaths','sum'),
               max_new_deaths_country = ('new_deaths','max'),
               total_new_tests = ('new_tests','sum'),
               total_countries_reported = ('location','nunique')
              ).reset_index().tail(5)
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2020.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2020.png)

# **2. Plotagem de dados usando Plotly( )**

O principal trabalho de um analista de dados é visualizar os dados. Cada DataFrame em Pandas tem uma API de plot () para plotagem. 

Por padrão, Pandas usa Matlplotlib como um backend para a trama. Existem vários outros backends que você pode usar. 

Aqui, usaremos a biblioteca [Plotly](https://plotly.com/python/plotly-express/) e configurá-la como os pandas plotando backend. Deveremos instalar a biblioteca plotly:

```python
# if using anaconda distribution (recommended)
conda install -c conda-forge plotly

# if using pip
pip install plotly
```

## **Novos Casos relatados por cada país para cada dia.**

Digamos que precisamos traçar novos casos relatados por cada país para cada dia. Podemos fazer isso usando:

```python
# generating a bar plot
data.plot.bar(x='date', y='new_cases', color='location')
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2021.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2021.png)

## **Top 10 países com base no número de novos casos nos últimos 10 dias**

Para obter os principais países, primeiro precisamos agrupar os dados por 'localização' e depois plotá-lo usando:

```python
# Step 1: generating a new dataset based on each location i.e. country
# Step 2: doing the sum on new_cases followed by sorting
# Step 3: Selecting top 10 countries from the dataset
data.groupby(['location']).new_cases.sum().sort_values(ascending=False).head(10).plot.bar()
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2022.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2022.png)

# **3. Estilo de dados usando a API de estilo**

Muitas vezes precisamos alternar entre Excel e Pandas para fazer coisas diferentes, como formatar os dados ou adicionar alguns estilos. Pandas introduziram API **styling** que pode ser usado para estilizar o conjunto de dados em Pandas em si. Podemos fazer várias operações usando estilo. Vamos passar por alguns exemplos.

## **Converter números em separados por vírgulas.**

Em nosso conjunto de dados, new_cases, new_deaths e new_tests são armazenados como um valor flutuante que não se encaixa para apresentação. Usando estilos podemos alterá-los para valores separados por címulas como

```python
# formatting the data to show numbers as comma separated
data.style.format({'new_cases':'{0:,.0f}',
'new_deaths':'{0:,.0f}',
'new_tests':'{0:,.0f}',}).hide_index()
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2023.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2023.png)

Podemos usá-lo para fazer outras coisas extravagantes, como adicionar um sinal de moeda para o campo de quantidade, alterar o número de pontos decimais, etc.

## **Destacando os valores máximos.**

Muitas vezes, precisamos destacar o valor máximo na coluna. Pode ser feito usando:

```python
# This will highlight the maximum for numeric column
data.style.highlight_max().hide_index()
```

## Formatação condicional com Pandas:

[Styling - pandas 1.2.0 documentation](https://pandas.pydata.org/pandas-docs/stable/user_guide/style.html)

## **Mapa de cores baseado na magnitude dos valores.**

## background_gradient()

Às vezes, é útil ver um mapa de cores baseado na magnitude dos valores, ou seja, grandes valores exibidos com cor escura e pequenos valores com luz. Pandas Styling fornece uma API agradável que faz isso perfeitamente com uma linha de código:

```python
# Adding blue color map for each numeric field
data.style.hide_index().background_gradient(cmap='Blues')
```

# **4. Pivô- converter dados de formato longo para amplo**

Se você está familiarizado com o Excel, você teria ouvido falar de tabelas pivôs. O pivô pandas nos ajuda a converter dados longos, ou seja, armazenados em linhas para dados amplos, ou seja, em colunas. Pandas fornecem duas APIs diferentes para pivotar:

- Pivô
- mesa pivô

Vamos passar por cima de cada um usando alguns exemplos.

## **pivô( )**

Considere um problema que precisamos encontrar covid-19 novos casos mudando horas extras para os 10 principais países.

Primeiro, precisamos encontrar os 10 principais países para cada dia que podemos fazer usando abaixo do código

```python
# Step 1: create a group based on date and location

# Step 2: order it by number of new cases.
grouped_data = data.groupby(['date','location']).new_cases.sum().sort_values(ascending=False)
# we have data for each date grouped by location.
grouped_data.head(5)
Output:
date        location     
2020-07-30  United States    74985.0
            Brazil           69074.0
2020-07-31  United States    68032.0
2020-08-01  United States    67023.0
2020-08-07  India            62538.0
```

```python
# Next we need to select top 10 countries for each date
# Step 3: create a new group based on date. 
# Step 4: select top 10 records from each group.
top10_countries = grouped_data.groupby('date').head(10).reset_index()
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2024.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2024.png)

Agora, temos os 10 melhores países para cada dia, mas isso é armazenado no formato longo, ou seja, para cada dia temos várias linhas. Podemos usar o pivô para converter esses dados em amplo formato usando:

```python
# Step 5: pivoting data on date and location
top10_countries_pivot = top10_countries.pivot(index='date', 
columns='location', 
values='new_cases')
```

No comando acima, estamos dizendo que para cada data, criar novas colunas para cada local com os valores que temos para new_cases. Isso resultará em:

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2025.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2025.png)

## Seaborn

Em seguida, podemos gerar um bom mapa de calor para os dados pivotados diretamente usando o Seaborn:

```python
# Step 6: plotting heatmap using Seaborn
sns.heatmap(top10_countries_pivot, annot=True, fmt='.0f')
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2026.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2026.png)

## **pivot_table.**

No caso acima, tínhamos apenas uma linha para a combinação de (data, localização) ou seja, para 2020-08-07, tínhamos apenas uma linha para 'Índia'. 

**E se precisarmos encontrar o número de novos casos para cada continente?** Neste caso, teríamos várias linhas para cada continente em uma determinada data, ou seja, o número de linhas seria igual ao número de países do continente. 

Para superar esse problema, a Pandas fornece **pivot_table() API que pode agregar registros para convertê-lo em uma única linha**. Vamos ver como isso pode ser feito:

### Criando pivot por continente

```python
# Creating a pivot table for continent
# We do not need to select top 10 records here as we have only 6 continents
# Notice the aggfunc below, it will actually sum the new_cases for each country in the continent.
continent_pivot = filtered_data.pivot_table(index='date',
columns='continent', values='new_cases', aggfunc='sum')
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2027.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2027.png)

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2028.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2028.png)

## **5. Utilizando idxmin( ), idxmax( )**

Como você acha que o país tem casos mínimos ou máximos na tabela de pivôs? Podemos fazê-lo usando idxmin() ou idxmax(). O Idxmin() nos dá o índice do valor mínimo para um determinado eixo, ou seja, linhas ou colunas e idxmax() nos dá o índice do valor máximo.

```python
# find country with maximum cases 
# axis=1 to find max in the row, default is column
top10_countries_pivot.idxmax(axis=1)
Output:
date
2020-07-29    United States
2020-07-30    United States
2020-07-31    United States
2020-08-01    United States
2020-08-02    United States
2020-08-03            India
2020-08-04            India
2020-08-05    United States
2020-08-06           Brazil
2020-08-07            India
```

```python
# find country with minimum cases
# axis=1 to find max in the row, default is column
top10_countries_pivot.idxmin(axis=1)
# This is among the top 10 countries
Output:
date
2020-07-29      Bangladesh
2020-07-30      Bangladesh
2020-07-31     Philippines
2020-08-01     Philippines
2020-08-02     Philippines
2020-08-03     Philippines
2020-08-04            Peru
2020-08-05    South Africa
2020-08-06           Spain
2020-08-07           Spain
```

## **6. MultiIndex usando set_index ( )**

Pandas suportam multi-indexação para linhas e colunas. Isso é útil para responder a perguntas simples. Por exemplo, se precisarmos encontrar dados —

- para um dia específico para um continente específico.
- para um local específico em um dia específico.
- alguns locais em alguns dias.

Existem muitas maneiras de fazer isso, mas vamos ver como é fácil usar multiíndice. Primeiro, criar vários índices usando a API set_index:

```python
# Creating Index on continent, location and date
# The index will be created in the order supplied
indexed_data = data.set_index(['continent','location','date']).sort_index()
# values of the index
indexed_data.index.values
Output:
array([('Africa', 'Algeria', '2020-07-29'),
       ('Africa', 'Algeria', '2020-07-30'),
       ('Africa', 'Algeria', '2020-07-31'), ...,
       ('South America', 'Venezuela', '2020-08-05'),
       ('South America', 'Venezuela', '2020-08-06'),
       ('South America', 'Venezuela', '2020-08-07')], dtype=object)
```

Agora, temos vários índices para cada linha, ou seja, para consultar a primeira linha, precisamos fazer:

```python
indexed_data.loc[(‘Africa’,’Algeria’,’2020–07–29')]
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2029.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2029.png)

Vamos ver alguns exemplos de como criar um multiíndice é útil.

## O **número de novos casos notificados nos EUA (Localização) da América do Norte (Continente) em 7 de agosto de 2020.**

```python
indexed_data.loc[('North America','United States','2020-08-07'),
'new_cases']

Output:
59755.0
```

## **Novos casos notificados na Ásia em 7 de agosto de 2020**

Aqui gostaríamos de obter dados para todos os países da Ásia. Podemos fazê-lo passando fatia (Nenhum) no local de localização que significa obter todos os locais.

```python
indexed_data.loc[('Asia',slice(None),'2020-08-07'),'new_cases']
Output(a snippet):
continent  location              date      
Asia       Afghanistan           2020-08-07       41.0
           Armenia               2020-08-07      233.0
           Azerbaijan            2020-08-07      144.0
           Bahrain               2020-08-07      375.0
           Bangladesh            2020-08-07     2977.0
           Bhutan                2020-08-07        3.0
           Brunei                2020-08-07        0.0
           Cambodia              2020-08-07        0.0
           China                 2020-08-07      132.0
           Georgia               2020-08-07        0.0
           India                 2020-08-07    62538.0
```

## **Novos casos notificados na Índia e nos Estados Unidos nos dias 6 e 7 de agosto**

Podemos passar uma lista de valores para qualquer índice. Neste exemplo, não estamos fornecendo o continente e selecionando vários valores para localização e data.

```python
indexed_data.loc[(slice(None),[‘India’,’United States’],[‘2020–08–06’,’2020–08–07']),’new_cases’]Output:
continent      location       date      
Asia           India          2020-08-06    56282.0
                              2020-08-07    62538.0
North America  United States  2020-08-06    52804.0
                              2020-08-07    59755.0
Name: new_cases, dtype: float64
```

Podemos fazer muitas coisas com multiíndice. Para aprender mais do que se referir a um bom artigo escrito por Byron Dolon 'How to Use MultiIndex in Pandas to Level Up Your Analysis':

[How to Use MultiIndex in Pandas to Level Up Your Analysis](https://towardsdatascience.com/how-to-use-multiindex-in-pandas-to-level-up-your-analysis-aeac7f451fce)

## **7. Combinando o MultiIndex em um único índice.**

Muitas vezes, quando fazemos agregação, temos índices MultiColumn como:

```python
# multiple aggregations on new_cases
grouped_data = data.groupby('date').agg({'new_cases':['sum','max','min']})
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2030.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2030.png)

Isso torna um pouco difícil obter os resultados reais. Podemos convertê-los em uma única coluna seguindo:

```python
# columns in grouped data
grouped_data.columns
Output:
MultiIndex([('new_cases', 'sum'),
            ('new_cases', 'max'),
            ('new_cases', 'min')],
           )
```

Combinar as colunas acima como new_cases_sum, new_cases_max new_cases_min usando o código simples:

```python
# here are we just joining the tuple with '_'
# this works for level-2 column indexes only
new_columns = ['%s%s' % (a, '_%s' % b if b else '') for a, b in grouped_data.columns]
new_columns
Output:
['new_cases_sum', 'new_cases_max', 'new_cases_min']
# change grouped_data columns.
grouped_data.columns = new_columns
```

![Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2031.png](Pandas%20Processo%20de%20Ana%CC%81lise%20e2ac32b266734a8facc2e5afeaf895ba/Untitled%2031.png)