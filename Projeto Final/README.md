<img src="https://www.ufsm.br/app/uploads/sites/607/2020/04/Cabe%C3%A7alho-CORONA.jpg">

# **Bootcamp Data Science Aplicada - Projeto Final**   <img src="https://yt3.ggpht.com/ytc/AKedOLRszi3O39AB5-uw_1jkrxJppwegjToBgIKFIOqiiA=s900-c-k-c0x00ffffff-no-rj" width="45" height="45" align="right">

Em dezembro de 2019, na ciadade de Wuhan, China, foi reportado o primeiro caso do SARS-CoV-2. Após causar epidemiar locais, o vírus foi se espalhando pelo mundo, sendo declarada pandemia pela OMS em 11 de março de 2020. Desde então, o vírus tem causado uma imensa pressão em todos os sistemas de saúde mundial, rapidamente ocupando todos os leitos disponíveis de UTI. Por conta disso, o hospital Sìrio Libanês disponilizou [no Kaggle](https://www.kaggle.com/S%C3%ADrio-Libanes/covid19) um banco de dados com diversos dados clínicos de pacientes, como sexo, idade, doenças pré-existentes, resultados de exames de sangue, entre outros. O objetivo sendo: criar um modelo que preveja, baseando-se nesses dados clínicos, se o paciente precisará utilizar UTI ou não.

# O Projeto

## 1. Objetivo

Criar um modelo capaz de prever, beaseado em dados clínicos, se um paciente precisará utilizar a UTI ou não.

## 2. Materiais

Para realização deste projeto, foi utilizado a linguagem de programação Python v. 3.9.6. Todos os códigos foram criados e rodados no Google Colab. As seguintes bibliotecas foram utilizadas:

* pandas == 1.3.5
* numpy == 1.21.5
* matplotlib == 3.2.2
* seaborn == 0.11.2
* sklearn == 1.0.2
* scipy == 1.4.1
* joblib == 1.1.0

Os Notebooks contendo o projeto apresentam-se em seguida:
1. [Limpeza de Dados e Definição de Funções](https://colab.research.google.com/github/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Notebooks/Projeto_Final_Funcoes_e_Limpeza_de_Dados.ipynb#scrollTo=8R1aWz6RliTz)
2. [Análise Exploratória e Seleção do Modelos](https://colab.research.google.com/drive/15Y3QnSjN9s3WM5ZHH5DUlHRK9W-S3kYr#scrollTo=BFN_hGzE-6L_)

## 3. Métodos

### 3.1 Limpeza de dados

A limpeza de dados se deu em 6 etapas:

1. Preenchimento de NaNs
2. Retirar pacientes que foram direto à UTI
3. Selecionar somente a janela 0-2 dos pacientes
4. Transformação de variáveis em string em categóricas
5. Retirar variáveis com variância 0
6. Selecionar variáveis com alta correlação entre si (maior que 0.95) e retirar uma

Para mais detalhes sobre a realização dessa etapa, visite o [Notebook de Limpeza de Dados e Definição de Funções](https://colab.research.google.com/github/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Notebooks/Projeto_Final_Funcoes_e_Limpeza_de_Dados.ipynb#scrollTo=8R1aWz6RliTz)

### 3.2 Análise Exploratória

Aqui, foram criados diferentes gráficos de barra, analisando a relação entre a ida ou nâo à UTI e as variáveis GENDER, AGE_ABOVE65 e AGE_PERCENTIL. 

### 3.2 Seleção do Modelo e seus Hiperparâmetros

Aqui, foi utilizada o RandomizedSearchCV para avaliar 4 tipos diferentes de modelos, com diferentes configurações de hiperparâmetros. Os modelos testados, e suas respectivas classes, foram:

1. Regressão Logística - Linear Model
2. Random Forest - Ensemble
3. C-Support Vector Classification (SVC) - Support Vector Machine (SVM)
4. Multi-layer Perceptron Classifier - Neural Network

Com isso, o modelo com melhor performance foi selecinado. Seus hiperparâmetros foram, então, aprimorados novamente, desta vez com o GridSearchCV.

### 3.3 Testes do Modelo

O modelo foi treinado no grupo treino e testado no grupo teste. Para avaliação, seu valor de auc foi calculado. Também foram feitas sua matriz de confusão de curva AUC - ROC

### 3.4 Construção do Modelo Final

Com resultados satisfatórios, o modelo final foi construído e exportado.

## 4. Resultados e Discussão

### 4.1 Análise Exploratória

Primeiro, foi analisada a relação da variável Gênero com as internações na UTI. Como os dados são anonimizados, não sabemos a qual gênero cada categoria significa. Ao analisar o gráfico, podemos ver que mais pacientes do gênero 0 foram à UTI do que não foram à UTI. Já para o gênero 1, a maioria dos pacientes não foi à UTI. Assim, podemos ver que **a proporção de pacientes que foi à UTI é maior no gênero 0**.

<img src="https://github.com/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Imagens/Gr%C3%A1fico%201.png?raw=true">

Agora, analisaremos a variável se o paciente tem mais ou menos de 65 anos. Podemos observar que, nos pacientes abaixo de 65 anos, a maioria não foi à UTI. Já nos pacientes acima de 65 anos, o contrário foi observado.

Também é possível observar como a diferença de pacientes que foram e não foram à UTI, em ambos os grupos, é muito maior na comparação deste gráfico, no que no gráfico por gênero. Isso pode mostrar que o fato do paciente ter mais ou menos que 65 anos é mais relevante do que seu gênero.

<img src="https://github.com/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Imagens/Gr%C3%A1fico%202.png?raw=true">

Agora, observamos o percentil de idade. Esta variável nos mostra, nos 10º, os 10% pacientes mais novos, no 20º, os 20% , e assim por diante.

Analisando o gráfico, é claro como o número de pacientes que vâo à UTI tendo a aumentar diretamente relacionado ao percentil da idade. Esse é um grande indicativo que, quanto maior a idade, maior o risco do paciente ir à UTI.

<img src="https://github.com/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Imagens/Gr%C3%A1fico%203.png?raw=true">

### 4.2 Testes de Modelo

A procura no RandomizedSearchCV gerou os seguintes resultados:

<img src="https://github.com/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Imagens/Resultados%20Geral.png?raw=true">

Assim, podemos ver que o modelo de Random Forest apresentou melhor performance. Os melhores hiperparâmetros selecionados são:

* bootstrap: True 
* criterion: 'gini' 
* max_depth: 3 
* min_samples_leaf: 40
* min_samples_split: 34
* n_estimators: 182

Com isso, iremos aprimorar os hiperparâmetros do RandomForest, utilizando GridSearchCV. Ele apresentou o seguinte resultados:

* best_score: 0.791515
* best_params: 
  * bootstrap: True
  * max_depth: 3
  * min_samples_leaf: 30
  * min_samples_split: 30
  * n_estimators: 100

### 4.3 Testes do Modelo com Hiperparâmetros Finais

Aqui, o modelo foi treinado, com os hiperparâmetros aprimorados do Random Forest, no grupo treino e testado no grupo teste. Foi feita a matriz de confusão de curva AUC - ROC deste modelo:


<img src="https://github.com/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Imagens/Matria%20de%20confus%C3%A3o.png?raw=true">

Aqui, podemos observar como o modelo obteve:

* Verdadeiro Positivo: 15
* Verdadeiro Negativo: 32
* Falso Positivo: 6
* Falso Negativo: 13

Neste caso, um Falso Positivo indica um paciente que não iria à UTI, mas o modelo indicou que ele iria.

Já um Falso Negativo, indica um paciente que iria à UTI, mas o modelo indicou que ele não iria.

A pesar de ambos serem relevantes, o Falso Negativo tem maior peso, pois ele mostra um caso em que, como o modelo indicou que o paciente não iria à UTI, o hospital pode não preparar este leito e o paciente ficar sem UTI. Neste quesito, o modelo apresentou um resultado não satisfatório e pode ser melhorado.

<img src="https://github.com/arturcgs/BootcampDataScienceAplicada3/blob/main/Projeto%20Final/Imagens/Curva%20AUC%20ROC.png?raw=true">

A curva AUC - ROC apresentou-se satisfatória. Idealmente, a curva passaria mais perto do ponto (0, 1). O AUC, porém, obteve um valor bom.

## 5. Conclusões

Neste projeto, foi utilizado um banco de dados do hospital Sírio Libanês, com dados clínicos de pacientes reais, visando a construção de um modelo que auxiliasse o hospital a entender melhor a necessidade de UTI de novos pacientes. Os dados foram limpos e organizados, pacientes não relevantes ao modelos foram excluídos, e variáveis não relevantes também foram excluídas. 

O conjunto de dados foi explorado, e chegou-se a conclusão que o gênero pode influenciar na necessidade de UTI, mas a idade parece ser um fator muito mais importante.

Quatro tipos de modelos foram testados:
* Linear Regression
* Random Forest
* SVC
* MLP CLassifier

Destes, o Random Forest apresentou melhores resultados. Seus hiperparâmetros, então, foram aprimorados. Com isso, um modelo de Random Foresto foi criado e testado, apresentando resultados satisfatórios. Este modelos, então, foi salvo e exportado.

Neste projeto, aprendi muito sobre diversos aspectos da ciência de dados, como improtação de dados, limpeza de dados, avaliação de relevância dos dados, interpretação dos dados, testes de diferentes tipos de modelos, testes de diferentes hiperparâmetros, testes de qualidade de modelo, entre outros aprendizados. 

## 6. Possíveis Melhorias

A pesar do modelo final apresentar características satisfatórias, diversas melhorias podem ser aplicadas neste estudo. Algumas delas incluem:
* Análise Exploratória mais profunda, entendo melhor a relação entre as variáveis
* Teste de mais tipos de modelos
* Testes de maior variedade de hiperparâmetros
* Aplicação de mais métodos de avaliação de qualidade nos modelos

## 7. Referências

[Bootcamp DataScience Aplicada - Alura](https://bootcamps.alura.com.br/bootcamp-data-science-3)
[scikit-learn](https://scikit-learn.org/stable/)
[seaborn](https://seaborn.pydata.org/)
[Vídeo sobre GridSearchCV](https://www.youtube.com/watch?v=HdlDYng8g9s&t=1s&ab_channel=codebasics)
[Vídeo sobre AUC e ROC](https://www.youtube.com/watch?v=4jRBRDbJemM&t=79s&ab_channel=StatQuestwithJoshStarmer)
