# House Prices
Repositório criado para **[competição do Kaggle "House Prices - Advanced Regression Techniques"](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/overview)**

O histórico dos resultados obtidos é mostrado abaixo e pode ser encontrado no Kaggle:
<img src="https://github.com/PedroALage/House_Prices/blob/main/pkgImagens/grafEvolucao.png"/>

## Etapa 1: Tratamento simples e modelo
- Arquivo: [**Parte1**](https://github.com/PedroALage/House_Prices/blob/main/Parte1.ipynb)
- Nessa etapa foram realizados apenas tratamentos básicos para conseguir verificar qual seria o resultado sem fazer nenhum tratamento nem engenharia dos dados
- Os valores vazios foram substituídos por -1 e as colunas de texto eliminadas
- Foram utilizados os algoritmos de **Regressão Linear**, **Árvore de Regressão** e **KNeighborsRegressor** para criar os modelos
- Os resultados foram avaliados utilizando o erro médio absoluto e o erro quadrático médio, dando preferência ao segundo, pois era o critério usado na competição
- O score retornado pelo Kaggle foi: 0,2547

## Etapa 2: Limpeza dos dados
- Arquivos: [**Parte2**](https://github.com/PedroALage/House_Prices/blob/main/Parte2.ipynb) | [**Modelos2**](https://github.com/PedroALage/House_Prices/blob/main/Modelos2.ipynb)
- Foram analisados os valores vazios e informações faltantes para escolher a melhor estratégia de tratamento
- Alguns valores vazios representavam ausência das características, nesse caso a informação foi preenchida por valor que a representasse
- Nos casos em que a informação realmente estava ausente, os campos foram substituídos por tratamentos condizentes
- Foram utilizados os mesmos modelos da Etapa 1
- O score retornado pelo Kaggle foi: 0,1815

## Etapa 3: Tratamento dos dados
- Arquivos: [**Parte3**](https://github.com/PedroALage/House_Prices/blob/main/Parte3.ipynb) | [**Modelos3**](https://github.com/PedroALage/House_Prices/blob/main/Modelos3.ipynb)
- Foi utilizada a base gerada na etapa 2 como base
- Com os dados já tratados, foi analisada a correlação entre as variáveis numéricas e os valores mais frequentes das variáveis de texto
- Nas colunas do tipo texto foram eliminadas as colunas com muitos valores iguais e depois foi utilizada a lambda function para fazer o tratamento dos dados
- Foi utilizado o OneHotEncoder para tratar as variáveis que não possuíam relação de ordem e o OrdinalEncoder para aquelas ordenadas
- Foi feita uma análise mais profunda nas colunas de garagem para entender melhor esta categoria de variáveis. Não foi possível fazer a mesma análise para os outros grupos de colunas, devido ao tempo necessário para entendimento do negócio e aplicação dos tratamentos
- Foram utilizados os mesmos modelos da Etapa 1
- Nessa etapa, foram geradas 2 bases:
  - A primeira (_1) possuía apenas as colunas analisadas a fundo
    - Score retornado pelo Kaggle: 0,1917
  - A segunda (_2) possuía tratamentos genéricos para todas as colunas de texto
    - Score retornado pelo Kaggle: 0,4547

## Etapa 4: Adicionando novos modelos
- Arquivos: [**Modelos4**](https://github.com/PedroALage/House_Prices/blob/main/Modelos4.ipynb)
- Foram utilizados os modelos de regressão linear (modelo com melhor resultado anterior), RandomForestRegressor e XGBoost
  - XGBoost foi indicado pela documentação da competição
- Executando nas 2 bases:
  - Score Kaggle da primeira base (_1): 0,1546
  - Score Kaggle da segunda base (_2): 0,1526

## Etapa 5: Melhorando os parâmetros
- Arquivos: [**Modelos5**](https://github.com/PedroALage/House_Prices/blob/main/Modelos5.ipynb)
- Foi utilizado o GridSearchCV para determinar os melhores parâmetros para os novos modelos
- Como o RandomForest teve um menor erro quadrático e o XGBoost um menor erro absoluto, ambos foram utilizados para teste:
  - RandomForest:
    - Score Kaggle da primeira base (_1): 0,1565
    - Score Kaggle da segunda base (_2): 0,1565
  - XGBoost:
    - Score Kaggle da primeira base (_1): 0,1599
    - Score Kaggle da segunda base (_2): 0,1528 

