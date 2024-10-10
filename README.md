# Análise de Campos Eletromagnéticos de ERBs

Este projeto realiza uma análise dos campos eletromagnéticos medidos em Estações Rádio Base (ERBs) no Brasil. Utiliza dados de medições eletromagnéticas e localizações geográficas das ERBs, aplicando técnicas de machine learning para explorar padrões e construir modelos preditivos.

## Dados

- **Medições de Campos Eletromagnéticos:** [Fonte](https://dados.gov.br/dados/conjuntos-dados/medicoes-de-campos-eletromagneticos1)
- **Localizações das ERBs:** [Fonte](https://www.telecocare.com.br/mapaerbs/)

## Etapas do Projeto

### 1. Pré-processamento
- **DataFrames:** Criação de `df` (medições) e `dferb` (localização de ERBs).
- **Join:** Combinação dos dataframes em `mdf` para associar medições às ERBs.

### 2. Feature Engineering
- **Distância ERB-Ponto de Medição:** Cálculo usando a [Fórmula de Haversine](https://en.wikipedia.org/wiki/Haversine_formula).

### 3. Análise Exploratória de Dados (EDA)
- **Empresas e Tipos de Medição:** Dados de 8 empresas em 4086 municípios, com medições fixas e de faixa larga.
- **Mapas:** Extração de bounding boxes via [OpenStreetMap](https://www.openstreetmap.org/).

### 4. Clusterização
- **K-Means (k=5):** Clusterização das medições por regiões do Brasil.
- **DBSCAN:** Agrupamento de medições próximas, relacionado às regiões de campo Fresnel e Fraunhofer.

### 5. Correlação de Variáveis
- **Latitude/Longitude:** Altamente correlacionadas, devido à proximidade das medições e ERBs.
- **Valor Médio e % do Limite:** Correlação não-linear (% do Limite = 0.1275 * (Valor Médio)², correlação de 99,99%).

### 6. Modelagem Supervisionada
- Algoritmos: **LR, SGD, Ridge, Lasso, ElasticNet, KNR, DTR, ABR, RF**.
- **Curvas de Aprendizado:** Overfitting em KNR e DTR; underfitting no ABR.

### 7. Feature Engineering Avançada
- **Novas Features:** Potência, Ganho, Altura (Tx/Rx), Frequência.
- **Impacto:** Melhorias no desempenho dos modelos após a inclusão dessas variáveis.

## Melhorias Futuras
- Filtragem de outliers.
- Explorar novas expressões matemáticas (inclinação das antenas).
- Otimização dos modelos.

## Referências

- [Análise da Intensidade de Campo Elétrico de Estações Rádio-Base](https://www.inatel.br/revista/busca/144-5-analise-da-intensidade-de-campo-s504918-1/file)
- [Wibowo et al., 2010 - Electric Field Intensity](https://core.ac.uk/download/pdf/42954572.pdf)
- [Arnold et al., 2010 - Power Consumption Modeling](https://www.semanticscholar.org/paper/Power-consumption-modeling-of-different-base-types-Arnold-Richter/da078d9f4c22c01e7acc4d85cc7bc929c61f3442/figure/2)
