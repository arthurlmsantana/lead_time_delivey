# 📦 Previsão de Lead Time de Delivery com Machine Learning

Este projeto tem como objetivo analisar e comparar o desempenho de cinco algoritmos de Machine Learning na tarefa de prever o tempo de entrega de pedidos de comida por delivery. Utilizando um dataset público disponibilizado no Kaggle, o projeto foi desenvolvido em um ambiente Jupyter Notebook e inclui etapas de limpeza, análise exploratória de dados (EDA), engenharia de features e avaliação de modelos preditivos.

A proposta é entender quais variáveis mais influenciam no tempo de entrega e identificar o modelo com melhor performance para esse tipo de previsão, o que pode ser útil para empresas do setor de delivery otimizarem suas operações e oferecerem uma experiência mais precisa aos clientes.


## Análise exploratória de dados

Primeiramente a ideia é visualizar o dataset como uma tabela. Para isso, é utilizado o pacote Pandas para visualizar as primeiras linhas:

![image](https://github.com/user-attachments/assets/90d5988b-196d-4e5d-84c7-3e5e803bb3b4)


Temos colunas categóricas e numéricas, cada uma delas vai ser analisada de forma separada. Para colunas categóricas podemos analisar por valores únicos apresentados no dataset:

<img width="1300" height="408" alt="image" src="https://github.com/user-attachments/assets/b885e6da-e3ca-4dc6-9b54-80eec97b3523" />

Para variáveis numéricas, é aplicado o método describe() e analisado as estatísticas básicas descritivas.

<img width="1295" height="383" alt="image" src="https://github.com/user-attachments/assets/b4f0d498-9e0b-4ef3-b79d-51051d0bf4e8" />

## Limpeza do dataset

Já no passo anterior, removemos os registros com valores nulos (ausentes) já que é necessário que todas as informações sejam presentes para que o registro da entrega faça sentido. Além disso, a análise incial das distribuições das variáveis numéricas indicam a presença de outliers. 
Para detectar esses dados, é utilizado o método zcores onde é definido que quaisquer valores acima de 3 desvios-padrão da média é considerado um ponto que não representa a performance geral do processo:

<img width="1302" height="524" alt="image" src="https://github.com/user-attachments/assets/252b960a-bd58-42bf-8474-149b62387ca4" />











