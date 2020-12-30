# Criando Ambiente Virtual

Primeiramente, configurar rapidamente o ambiente de ciência de dados e usar diferentes bibliotecas python que podem acelerar o processo de aprendizagem.

O Machine Learning parece ser fascinante para muitos iniciantes, mas muitas vezes eles se perdem no pool de informações disponíveis em diferentes recursos. Isso é verdade que temos muitos algoritmos e passos diferentes para aprender, mas começando com uma base forte não só dá confiança, mas também a motivação para aprender e explorar mais. Aqui, passaremos pelas etapas sobre como configurar seu ambiente e começar a aprender com a ajuda de um conjunto de dados conhecido, ou seja, conjunto de dados **IRIS**, que é um problema de **classificação multiclasse** no Machine Learning. Também passaremos por algumas **bibliotecas de python úteis que podem acelerar o processo de aprendizagem que pode ajudá-lo mesmo se você for um cientista de dados**. 

# **Configuração do Meio Ambiente**

Usaremos a distribuição da Anaconda para configurar o ambiente de ciência de dados. Baixe a versão mais recente de Anaconda [daqui](https://www.anaconda.com/products/individual) e abra o **prompt anaconda** e execute o seguinte comando:

```python
jupyter notebook
```

O comando acima iniciará o servidor Jupyter e carregará o diretório do notebook no seu navegador.

## **Criar um ambiente virtual**

[Managing environments - conda 4.9.2.post14+2fcfec1a documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

Espero que esteja ciente dos ambientes virtuais, se não puder ler sobre eles [aqui.](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) Embora a Anaconda venha com um **ambiente básico** que está tendo a maioria das bibliotecas já instaladas, **recomenda-se usar ambientes virtuais**, pois eles nos ajudam a gerenciar diferentes ambientes que podem ter pacotes diferentes e se algo der errado com um ambiente não afetará outros. Aqui estão os comandos que você pode usar para criar, ativar e instalar pacotes no ambiente virtual.

```python
# create new environment 
conda create --name your_env_name

# activate the environment
conda activate your_env_name

# installing package
conda install -c conda-forge package_name
```

## **Link ambiente virtual com o Notebook**

Por padrão, o **novo ambiente não apareceria no notebook Jupyter**. Precisariamos executar seguintes comandos para vincular o ambiente com o cliente Jupyter:

```python
# install pip if it is not installed in the environment
conda install -c conda-forge pip

# install ipykernel
pip install --user ipykernel

# link with notebook
python -m ipykernel install --user --name=your_env_name
```

## **Notebook inicial e comandos úteis**

Depois de ter um ambiente virtual, vá até o navegador e abra um novo notebook como mostrado abaixo. Selecione o ambiente que você acabou de criar.

![Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled.png](Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled.png)

O notebook Jupyter fornece muitos atalhos úteis. Abaixo de 2 estão meus favoritos...

1. **Tab: isso age como um autocomplete.**
2. **Shift + Tab: isso dará os detalhes do comando e você não precisa ir à documentação da biblioteca toda vez.**

[](https://miro.medium.com/max/750/1*iXQCyyVrHGmNa9UIZ1m2XQ.gif)

# **Explorando bibliotecas Python e aplicando machine learning**

Precisamos ter bibliotecas diferentes para carregar os conjuntos de dados, visualizações e modelagem. Vamos passar por cada um e instalá-los no ambiente. Você pode dar uma olhada no meu notebook, sinta-se livre para baixá-lo e importá-lo em seu ambiente e brincar com ele-

```python
conda install -c conda-forge jupyter_contrib_nbextensions
```

## **Jupyter Contrib Nbextensions**

Muitas vezes precisamos compartilhar nosso caderno com diferentes stakeholders ou talvez precise apresentá-los, esta biblioteca nos fornece muitas extensões diferentes. Eu não vou passar pelas extensões aqui, mas eu recomendo usar isso. Meus favoritos são...

1. Títulos dobráveis.
2. Tabela de Conteúdo.
3. Tempo de execução.

Podemos instalá-lo usando:

```python
conda install -c conda-forge jupyter_contrib_nbextensions
```

## **Pandas- Python Data Analysis Library**

Este é o coração da ciência de dados com python e fornece muitas capacidades diferentes como

- Estruturas de dados para trabalhar com os dados.
- Operações que você pode executar nos dados.
- Carregar e salvar dados em diferentes formatos.

e muitos mais. Muitas outras bibliotecas que usamos para aprendizado de máquina com python têm pandas como dependência. Instale-o usando...

```
conda install -c conda-forge pandas
```

O comando acima instalará outras bibliotecas como o NumPy que os pandas usam sob o capô.

## **Sklearn (Scikit-Learn)**

Usaremos esta biblioteca para baixar conjuntos de dados de teste e aplicar diferentes algoritmos de aprendizado de máquina. Instale usando o seguinte comando.

```python
conda install -c conda-forge scikit-learn
```

Em problemas **de classificação** de aprendizado de máquina, o problema pode ser entendido como para recursos X (variáveis de entrada) prever y (valor-alvo). Sklearn fornece poucos conjuntos de dados de teste que podemos usar para jogar, levaremos o conjunto de dados IRIS para este exercício, mas se você quiser brincar com os outros, então você pode se referir a [isso](https://scikit-learn.org/stable/datasets/index.html).

Scikit-learn 0.23.1 adicionou um recurso pelo qual podemos retornar o conjunto de dados do teste diretamente no dataframe X e y. Certifique-se de que está executando a versão 0.23.1.

```python
from sklearn.datasets import load_iris
```

![Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled%201.png](Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled%201.png)

Agora vamos passar pelas outras bibliotecas e vamos usar Sklearn para modelar mais tarde

## pandas-profiling

Ele fornece um rico relatório de perfil para os dados que fornece um monte de informações de valores perdidos a correlações. Você precisa **instalá-lo usando pip** como conda-package baixa versão antiga dele.

```python
pip install --user pandas-profiling
```

![https://miro.medium.com/max/750/1*knV7VkJboi-Vsg0OgQGe8A.gif](https://miro.medium.com/max/750/1*knV7VkJboi-Vsg0OgQGe8A.gif)

[](https://miro.medium.com/max/750/1*knV7VkJboi-Vsg0OgQGe8A.gif)

Este relatório fornece muitos detalhes, dos quais poucos são...

1. Visão geral de diferentes variáveis no conjunto de dados.
2. Correlação entre variáveis.
3. Interações entre variáveis.
4. Detalhes sobre cada variável.

Os seguintes comandos podem ser usados para gerar e salvar o relatório de perfil:

```python
# import ProfileReport 
from pandas_profiling import ProfileReport

# generate the profile report and save it to a variable
profile_report = ProfileReport(your_dataframe)

# save to html format
profile_report.to_file('pandas_profiling_report.html')

# load as widget in the notebook, you might need to install pywidgets
profile_report.to_widgets()
```

## **Plotly**

Embora o perfil de pandas forneça muitas informações úteis, ainda precisamos visualizar diferentes informações, como por exemplo, precisamos descobrir como a variável alvo é distribuída entre múltiplas variáveis de entrada. Existem muitas bibliotecas para visualização, Matlplotlib e Seaborn são as famosas que você teria ouvido falar. A principal coisa em que plotly se destaca são os **enredos interativos,** ou seja, você pode interagir com as parcelas geradas. Instale-o usando o seguinte comando:

```python
conda install -c conda-forge plotly
```

Abaixo, traçamos um gráfico de dispersão entre o comprimento do sepala com comprimento de pétala e usamos 'cor' para mostrar como a variável alvo está relacionada.

```python
# import plotly express
import plotly.express as plotly_express

# plot between sepal length and petal length with target
plotly_express.scatter(X, x='sepal length (cm)', y='petal length (cm)', \
                          color=y.astype('category'))

# plot between sepal width and petal width with target
plotly_express.scatter(X, x='sepal width (cm)', y='petal width (cm)', \
                          color=y.astype('category'))
```

Podemos filtrar diferentes alvos, vide abaixo:

![https://miro.medium.com/max/750/1*t9l6cNX0qeioWUooFypx4g.gif](https://miro.medium.com/max/750/1*t9l6cNX0qeioWUooFypx4g.gif)

Esta biblioteca fornece um monte de funcionalidade adicional, talvez possamos cobrir isso em uma história diferente.

## **Conjunto de dados de treinamento e teste**

A ideia de gerar modelos é prever valores que não são conhecidos. Se aprendermos o modelo em todo o conjunto de dados, então não poderemos avaliar como ele se sai nos dados invisíveis. Para isso, dividimos o conjunto de dados em conjunto de dados de treinamento e teste. Um conjunto de dados de treinamento é usado para treinar o modelo e o conjunto de testes é usado para avaliar o modelo. Sklearn fornece uma função 'train_test_split' que divide o conjunto de dados em conjuntos de dados de trem e teste. O código a seguir pode ser usado para dividir os conjuntos de dados.

```python
from sklearn.model_selection import train_test_split
```

![Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled%202.png](Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled%202.png)

## **Sintonizando hiperparmetros**

Uma das tarefas importantes no aprendizado de máquina é sintonizar hiperparmetros, esses parâmetros são os diferentes atributos do algoritmo que controlam o processo de aprendizagem. Diferentes valores são adequados para diferentes problemas de aprendizagem e é importante descobrir os melhores parâmetros. O Sklearn fornece principalmente duas maneiras de 'GridSearchCV' e 'RandomizedSearchCV' para encontrar os melhores parâmetros. Para grandes conjuntos de treinamento, talvez precisemos usar randomizedSearchCV, pois levará muito tempo para aprender todos os parâmetros. No conjunto de dados IRIS, temos apenas 150 linhas e, portanto, usamos 'GridSearchCV'.

Para esta história, vamos treinar o modelo de Região Logística que é adequado para problemas de classificação e tem diferentes hiperparmetros como 'solver', 'C', 'penalty' e 'l1-ratio'. Nem todos os solucionadores suportam todos os parâmetros e, portanto, criamos dicionários diferentes para todos os solucionadores diferentes.

```python
# import LogisticsRegression
from sklearn.linear_model import LogisticRegression

# import GridSearchCV
from sklearn.model_selection import GridSearchCV

# create a LogisticsRegression instance
logistics_regression = LogisticRegression(random_state=0, max_iter=10000)

# define parameters grid
parameters = [
    {
        'penalty': ['l1'], 
        'solver': [ 'liblinear', 'saga'],
        'C': [0.001, 0.01, 0.1, 1, 10, 100, 1000],
    },
    {
        'penalty': ['l2'], 
        'solver': ['newton-cg', 'lbfgs','sag','saga'],
        'C': [0.001, 0.01, 0.1, 1, 10, 100, 1000],
    },
    {
        'penalty': ['elasticnet'], 
        'solver': ['saga'],
        'C': [0.001, 0.01, 0.1, 1, 10, 100, 1000],
        'l1_ratio':[.1, .5, .7, .9, .95, .99, 1]
    }   
]

# Define GridSearchCV
grid_search = GridSearchCV(logistics_regression, param_grid = parameters)

# fit GridSearchCV
model = grid_search.fit(X_train, y_train)

# find the best estimator 
print (model.best_estimator_)

# predict y values
y_pred = model.predict(X_test)
```

O código acima procuraria diferentes combinações de parâmetros e encontraria o melhor que melhor generaliza o problema.

## **Avaliando o modelo**

Como mencionamos, precisamos avaliar o modelo no conjunto de dados do teste, muitas métricas diferentes estão disponíveis. A comum é a precisão para problemas de classificação. Aqui mostraremos a precisão, classification_report e a matriz de confusão que Sklearn fornece.

![Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled%203.png](Criando%20Ambiente%20Virtual%2036642e535326468d9d7e3e8fe2950f25/Untitled%203.png)

O conjunto de dados IRIS é classificado como um conjunto de dados fácil, o que significa que os dados já são adequados para fins de aprendizado de máquina e, portanto, conseguimos obter uma pontuação perfeita, ou seja, pontuação de precisão de 1.0 com o nosso modelo. Isso significa que nosso modelo previu todas as amostras no conjunto de dados do teste corretamente. Vai variar com os diferentes problemas que você está tentando resolver.