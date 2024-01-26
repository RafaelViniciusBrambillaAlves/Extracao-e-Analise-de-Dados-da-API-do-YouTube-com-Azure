# Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure

Este projeto envolve a extração e análise de dados dos 50 vídeos mais populares do YouTube Brasil, utilizando a API do YouTube. As etapas são executadas em notebooks do Databricks, com armazenamento e orquestração na plataforma Azure.

## Bronze
Extração de Dados com YouTube API e Armazenamento no Blob "bronze"
O primeiro notebook, coleta_de_dados.ipynb, utiliza a API do YouTube para coletar dados brutos dos 50 vídeos mais populares no Brasil. Os dados são armazenados em um Blob Storage chamado "bronze" na Azure.

## Silver
Pré-processamento com Pandas e Armazenamento no Blob "silver"
O segundo notebook, tratamento_de_dados.ipynb, acessa os dados brutos no Blob "bronze". Utilizando a biblioteca Pandas, realizamos tarefas de pré-processamento, incluindo exclusão de colunas desnecessárias, formatação de colunas e renomeação. O resultado é salvo no Blob "silver".

## Gold
Análise e Visualização no Databricks, com Salvamento no Blob "gold"
O terceiro notebook, visualizacao_de_dados.ipynb, acessa os dados tratados no Blob "silver". Utilizando as capacidades de visualização e análise do Databricks, realizamos análises exploratórias e geramos gráficos que fornecem insights sobre os vídeos. Os gráficos são salvos em uma pasta no Blob "gold".

## Orquestração com Azure Data Factory
Toda a orquestração do fluxo de trabalho é realizada pelo Azure Data Factory. O arquivo etl_pipeline.json garantem a execução sequencial e automática dos notebooks em cada etapa do projeto, (extração, tratamento e visualização).
