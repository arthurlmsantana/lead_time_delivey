# 📦 Previsão de Lead Time de Delivery com Machine Learning

Este projeto tem como objetivo analisar e comparar o desempenho de cinco algoritmos de Machine Learning na tarefa de prever o tempo de entrega de pedidos de comida por delivery. Utilizando um dataset público disponibilizado no Kaggle, o projeto foi desenvolvido em um ambiente Jupyter Notebook e inclui etapas de limpeza, análise exploratória de dados (EDA), engenharia de features e avaliação de modelos preditivos.

A proposta é entender quais variáveis mais influenciam no tempo de entrega e identificar o modelo com melhor performance para esse tipo de previsão, o que pode ser útil para empresas do setor de delivery otimizarem suas operações e oferecerem uma experiência mais precisa aos clientes.


## Análise exploratória de dados

A primeira etapa do projeto consiste em explorar o dataset visualmente, compreendendo sua estrutura, tipos de variáveis e possíveis inconsistências. Para isso, utilizamos a biblioteca Pandas para carregar os dados e visualizar as primeiras linhas da tabela, facilitando o entendimento inicial do conjunto de dados:

![image](https://github.com/user-attachments/assets/90d5988b-196d-4e5d-84c7-3e5e803bb3b4)


O dataset contém variáveis categóricas e numéricas, e cada tipo foi analisado separadamente para uma melhor compreensão dos dados.
Para as colunas categóricas, o foco está em identificar os valores únicos presentes no conjunto de dados, o que ajuda a entender a variedade de categorias e possíveis inconsistências ou valores inesperados.

<img width="1300" height="408" alt="image" src="https://github.com/user-attachments/assets/b885e6da-e3ca-4dc6-9b54-80eec97b3523" />

Para as variáveis numéricas, utilizamos o método .describe() do Pandas, que retorna um resumo estatístico com as principais medidas descritivas, como média, desvio padrão, valores mínimo e máximo, e os quartis.

<img width="1295" height="383" alt="image" src="https://github.com/user-attachments/assets/b4f0d498-9e0b-4ef3-b79d-51051d0bf4e8" />

## Limpeza do dataset

Já no passo anterior, removemos os registros com valores nulos (ausentes) já que é necessário que todas as informações sejam presentes para que o registro da entrega faça sentido. Além disso, a análise incial das distribuições das variáveis numéricas indicam a presença de outliers. 
Para detectar esses dados, é utilizado o método zcores onde é definido que quaisquer valores acima de 3 desvios-padrão da média é considerado um ponto que não representa a performance geral do processo:

<img width="1302" height="524" alt="image" src="https://github.com/user-attachments/assets/252b960a-bd58-42bf-8474-149b62387ca4" />

## Engenharia de Features
Antes de prosseguir para o treinamento de modelos de regressão, é necessário aplicar algumas técnicas de engenharia de features. 
A primeira é a Label-Encoding na variável "Traffic_Level", já que correspondem a uma relação de níveis de tráfego do mais baixo até o mais alto (ordenados por grau de dificuldade de transitar):

<img width="1301" height="525" alt="image" src="https://github.com/user-attachments/assets/034c84d0-3fd7-44f9-a856-a102c650e4aa" />

O One-Hot encoding é aplicado para as demais variáveis já que não há um número alto de categorias, portanto não gera um alto número de colunas com essa transformação:

<img width="1303" height="331" alt="image" src="https://github.com/user-attachments/assets/56fd5574-f5b6-4373-b6b9-261de8373ad4" />

## Visualização da relação de dados quantitativos:

<img width="986" height="1023" alt="image" src="https://github.com/user-attachments/assets/d2052546-0571-4a39-8016-e3254d5be5e8" />


## Treinando modelos
São testados 5 modelos de regressão nas condições padrão do pacote Scikit learn avaliando o coeficiente de determinação (R² ajustado) para cada um deles.

  1) Regressão Linear
  2) Decision Tree
  3) Random Forest
  4) SVR
  5) XGBoost

Cada um deles com split de 20% dos registros para dados de treinamento e 80% de dados de teste:

<img width="1029" height="480" alt="image" src="https://github.com/user-attachments/assets/36946713-11ff-489b-b241-09f5505a9c64" />

A regressão linear tem o melhor resultado entre os modelos à princípio. Porém, como os parâmetros da Random Forest (segundo modelo com melhor ajuste) podem ser tunados, vale o esforço de otimizar parâmetros desse modelo:

<img width="1309" height="582" alt="image" src="https://github.com/user-attachments/assets/fd317f8a-d247-4638-b59e-8f15dca92fb6" />

Houve um aumento no coeficiente de determinação e a aplicação desse modelo na performance de um processo de negócio tão aberto a variações é possível.

<img width="790" height="590" alt="image" src="https://github.com/user-attachments/assets/50e21696-2a3b-4a37-b840-1345badcfe89" />











