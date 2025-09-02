# Desafio Indicium - Predição de Nota IMDB

Este projeto consiste em uma análise e modelagem de dados para prever a nota de filmes no IMDB. A análise exploratória foi realizada para entender as relações entre as variáveis e a modelagem foi feita utilizando uma pipeline de machine learning para garantir um fluxo de trabalho eficiente e reprodutível.

## Estrutura do Projeto

* **`Desafio_ibm.ipynb`**: Notebook Jupyter contendo toda a análise exploratória, pré-processamento de dados e o treinamento do modelo.
* **`modelo_treinado.pkl`**: O modelo de machine learning treinado e serializado para uso na API.
* **`requirements.txt`**: Lista de dependências para reproduzir o ambiente do projeto.

## Análise e Conclusões

A análise exploratória dos dados revelou alguns pontos interessantes:
* **Correlação**: Foi observada uma correlação positiva entre o `IMDB_Rating` e variáveis como `Meta_score` e `Runtime`.
* **Limpeza de Dados**: As colunas `Runtime` e `Gross` continham caracteres que foram removidos para converter os dados para o tipo numérico. Valores ausentes (`Meta_score`, `Gross`, `Certificate`) foram tratados com a mediana ou preenchidos com uma categoria específica (`No certificate`).
* **Feature Engineering**: A coluna `Genre`, que continha múltiplos gêneros por filme, foi transformada em colunas binárias (`one-hot encoding`).

## Modelagem de Dados

Para a modelagem, foi utilizada uma abordagem de pipeline do `scikit-learn` para automatizar as etapas de pré-processamento e treinamento do modelo.

1.  **Pré-processamento**: A pipeline inclui transformadores para tratar dados ausentes, padronizar variáveis numéricas e binarizar variáveis categóricas.
2.  **Modelos Testados**: Foram testados modelos de regressão, incluindo `LinearRegression`, `RandomForestRegressor` e `GradientBoostingRegressor`.
3.  **Modelo Final**: O modelo `GradientBoostingRegressor` foi o que apresentou o melhor desempenho com base nas métricas de erro (MAE, MSE) e no coeficiente de determinação (R²), que explicou cerca de 42% da variância dos dados.


## Escolha de Modelo e motivações 

O problema em questão é de regressão, pois o objetivo é prever a variável IMDb Rating. A seleção das variáveis foi guiada pela análise exploratória: priorizaram-se colunas que apresentaram correlação significativa com o alvo, além de variáveis que, mesmo com correlação fraca, pudessem contribuir para explicar a variabilidade do resultado final.
Quanto à modelagem, optou-se pelo GradientBoostingRegressor devido à sua robustez e capacidade de lidar com relações complexas entre as variáveis, bem como com problemas de multicolinearidade, um fator relevante para este conjunto de dados. Por outro lado, sua principal desvantagem é a maior complexidade, que pode aumentar o risco de overfitting. No entanto, dado que a amostra não era suficientemente grande, esse problema não se manifestou de forma crítica.
Por fim, em relação às métricas de avaliação, optou-se por indicadores simples e de fácil interpretação: Erro Quadrático Médio (MSE), Erro Absoluto Médio (MAE) e Coeficiente de Determinação (R²). A escolha buscou equilibrar clareza na comunicação dos resultados e relevância para o contexto da análise.

