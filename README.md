# Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure

Este projeto envolve a extração e análise de dados dos 50 vídeos mais populares do YouTube Brasil, utilizando a API do YouTube. As etapas são executadas em notebooks do Databricks, com armazenamento e orquestração na plataforma Azure.

### Bronze
Extração de Dados com YouTube API e Armazenamento no Blob "bronze"
O primeiro notebook, coleta_de_dados.ipynb, utiliza a API do YouTube para coletar dados brutos dos 50 vídeos mais populares no Brasil. Os dados são armazenados em um Blob Storage chamado "bronze" na Azure. Os dados estão salvo no formato .csv como no exemplo na pasta 'blob_bronze'.

### Silver
Pré-processamento com Pandas e Armazenamento no Blob "silver"
O segundo notebook, tratamento_de_dados.ipynb, acessa os dados brutos no Blob "bronze". Utilizando a biblioteca Pandas, realizamos tarefas de pré-processamento, incluindo exclusão de colunas desnecessárias, formatação de colunas e renomeação. O resultado é salvo no Blob "silver".  Os dados estão salvo no formato .csv como no exemplo na pasta 'blob_silver'.

### Gold
Análise e Visualização no Databricks, com Salvamento no Blob "gold"
O terceiro notebook, visualizacao_de_dados.ipynb, acessa os dados tratados no Blob "silver". Utilizando as capacidades de visualização e análise do Databricks, realizamos análises exploratórias e geramos gráficos que fornecem insights sobre os vídeos. Os gráficos são salvos em uma pasta no Blob "gold".  Os graficos estão salvo no formato png como no exemplo na pasta 'blob_gold'.

### Orquestração com Azure Data Factory
Toda a orquestração do fluxo de trabalho é realizada pelo Azure Data Factory. O arquivo etl_pipeline.json garantem a execução sequencial e automática dos notebooks em cada etapa do projeto, (extração, tratamento e visualização).

### Tecnologias, Linguagens e Bibliotecas Utilizadas
  <div style="display: flex; flex-direction: row;">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/1200px-Python-logo-notext.svg.png" alt="Descrição da Imagem" width="40">
  <img src="https://cdn.icon-icons.com/icons2/2699/PNG/512/microsoft_azure_logo_icon_168977.png" width="100">
  <img src="https://upload.wikimedia.org/wikipedia/commons/6/63/Databricks_Logo.png" width="100">     
  <img src="https://miro.medium.com/v2/resize:fit:975/0*IOGNRnuhopjfGQzl.png" width="100"> 
  <img src="https://securiti.ai/wp-content/uploads/2023/03/microsoft-azure-blob-storage-logo.com_.webp" width="120">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Pandas_logo.svg/2560px-Pandas_logo.svg.png" width="100">
  <img src="https://matplotlib.org/stable/_images/sphx_glr_logos2_003.png" width="120">
   <img src="https://seaborn.pydata.org/_images/logo-wide-lightbg.svg" width="135">
</div>
