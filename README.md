# Curso 
POSTech de IA para Devs FIAP 

**Grupo 88**
 Diego Santos Arruda - RM 367255

 **Turma**
 7IADT
    
# Entregável
 - [Video de apresentação no Youtube]((https://vimeo.com/1133309204?share=copy&fl=sv&fe=ci))
 - [Arquivo Notebook no Colab Versão](https://colab.research.google.com/drive/1OojI1_roiQPwShd4tInm-blc2Gl9nkeY?usp=sharing)    
 - [Github](https://github.com/Diego1988Arruda/mba-ia-desafio-Modulo1.git)

# Introdução

Este projeto tem como objetivo a solução do desafio de criar a base de um sistema inteligente de suporte ao diagnóstico de câncer de mama, relacionado ao Tech Challenge Fase 1, do curso de Pós-Graduação de IA para Devs da FIAP. O trabalho visa acelerar a triagem e apoiar as decisões médicas através de Machine Learning.

# O Problema
O desafio consiste em implementar um sistema de IA focado em machine learning para a Classificação de Exames , especificamente o Diagnóstico de Câncer de Mama (maligno ou benigno), com base nas características do tumor.
A base de dados utilizada é o Breast Cancer Wisconsin Data (data.csv) do [Kaggle](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data?resource=download)

## Tarefas

### Exploração de dados
Carregar a base de dados e explorar suas características: O dataset foi carregado, contendo 569 amostras e 32 colunas (atributos). Uma coluna vazia ('Unnamed: 32') e a coluna 'id' foram removidas.
Analise estatísticas descritivas e visualize distribuições relevantes: Verificou-se que a variável alvo ('diagnosis') possui 357 casos Benignos (0) e 212 Malignos (1). Foi gerado um histograma da distribuição de diagnósticos e um gráfico de barras cruzadas para analisar a relação da malignidade por faixas de simetria (symmetry_mean)

### Pré-processamento de dados
Realizar a limpeza dos dados, tratando valores ausentes (se necessário): A análise inicial indicou que o dataset não possui dados nulos (isnull().sum() == 0) ou duplicados, não sendo necessária uma etapa de limpeza de valores ausentes.
Converta variáveis categóricas em formatos adequados para a modelagem: A variável categórica de diagnóstico ('diagnosis'), com rótulos 'B' e 'M', foi convertida em numérica (0 e 1) utilizando LabelEncoder. O dataset foi dividido em 80% para treinamento e 20% para teste (train_test_split)

### Modelagem
Criar um modelo preditivo de classificação utilizando uma técnica à sua escolha (por exemplo, Regressão Linear, Árvores de Decisão, etc): Foram criados e treinados três modelos: Regressão Linear, Random Forest e XGBoost.
Treinamento e avaliação do modelo:
•	O modelo XGBoost obteve o melhor desempenho no conjunto de teste, com um R² de 0.795.

 
### Validação estatísticas
Utilizar as métricas estatísticas para validar a eficácia do modelo (p-value, intervalo de confiança):
•	Foi aplicado o teste Shapiro-Wilk nos resíduos do modelo XGBoost. O p-valor obtido (1.88e-13) resultou na rejeição da hipótese nula, indicando que os resíduos não seguem uma distribuição normal (consideração importante, pois a natureza do problema é binária e não regressão linear tradicional).
•	O intervalo de confiança de 95% para a média das predições do XGBoost foi calculado como [0.343, 0.515].


### O que avaliaremos
Apresentar resultados visuais: Foi gerado um gráfico (diagnosis_dataset['diagnosis'].hist()) mostrando a distribuição das classes (Benigno e Maligno) e um gráfico de distribuição de malignidade por faixas de simetria (symmetry_mean).
Elabore um relatório que inclua uma análise de resultados, insights obtidos e validação estatística: A análise de Feature Importance do modelo XGBoost indicou que as características mais importantes para o diagnóstico são perimeter_worst, area_worst e radius_worst. O modelo, por ser uma base de IA, deve atuar apenas como suporte ao médico, que sempre deve ter a palavra final

### Observações
Espera-se que o modelo seja capaz de fazer predições confiáveis da malignidade de tumores com base nas características fornecidas. O modelo XGBoost atinge um desempenho de R² 0.795. No entanto, para uma avaliação completa do diagnóstico, recomenda-se o uso de métricas específicas de classificação como Acurácia, Precisão, Recall e F1-score, conforme sugerido nos próximos passos.

