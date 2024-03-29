# Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure

Este projeto envolve a extração e análise de dados dos 50 vídeos mais populares do YouTube Brasil, utilizando a API do YouTube. As etapas são executadas em notebooks do Databricks, com armazenamento e orquestração na plataforma Azure.

### Bronze 🥉
Extração de Dados com YouTube API e Armazenamento no Blob "bronze"
O primeiro notebook, coleta_de_dados.ipynb, utiliza a API do YouTube para coletar dados brutos em formato .json dos 50 vídeos mais populares no Brasil. Os dados são armazenados em um Blob Storage chamado "bronze" na Azure. Os dados estão salvo no formato .csv de exemplo na pasta 'blob_bronze'.

### Silver 🥈
Pré-processamento com Pandas e Armazenamento no Blob "silver"
O segundo notebook, tratamento_de_dados.ipynb, acessa os dados brutos no Blob "bronze". Utilizando a biblioteca Pandas, realizamos tarefas de pré-processamento, incluindo exclusão de colunas desnecessárias, formatação de colunas e renomeação. O resultado é salvo no Blob "silver".  Os dados estão salvo no formato .csv como no exemplo na pasta 'blob_silver'.

 Para o tratamento desses dados, foram excluido 28 colunas que não precisavam ser usadas, ouve a formatação e padronização de algumas colunas, divisão de dia e horário da publicação dos videos, criação do link completo para acessar os videos, padronização da duração dos vídeos para minutos e renomeação das colunas. 
 Esse é o resultado:

 | Coluna                | Descrição                                      |
|------------------------|-------------------------------------------------|
| tipo                   | Tipo de objeto, indicando que é um vídeo do YouTube. |
| id                     | Identificador único do vídeo.                   |
| titulo                 | Título do vídeo.                                |
| descricao              | Descrição do vídeo.                             |
| thumbnails_png         | URLs das imagens thumbnails em formato PNG.     |
| canal                  | Título do canal do YouTube.                     |
| tags                   | Lista de tags associadas ao vídeo.              |
| idioma                 | Idioma padrão do vídeo.                         |
| duracao                | Duração do vídeo.                               |
| definicao              | Definição do vídeo (por exemplo, HD).           |
| visualizacoes          | Número de visualizações do vídeo.               |
| likes                  | Número de curtidas no vídeo.                    |
| comentarios            | Número de comentários no vídeo.                 |
| Regioes_bloqueadas     | Regiões onde o vídeo está bloqueado.            |
| dia                    | Data de publicação do vídeo.                    |
| horario                | Horário de publicação do vídeo.                 |
| link                   | Link para o vídeo no YouTube.                   |

 

### Gold 🥇
Análise e Visualização no Databricks, com Salvamento no Blob "gold"
O terceiro notebook, visualizacao_de_dados.ipynb, acessa os dados tratados no Blob "silver". Utilizando as capacidades de visualização e análise do Databricks, realizamos análises exploratórias e geramos gráficos que fornecem insights sobre os vídeos. Os gráficos são salvos em uma pasta no Blob "gold".  Os graficos estão salvo no formato png como no exemplo na pasta 'blob_gold'.

Para a análise buscou-se responder 5 perguntas simples, com os dados do dia 24 / 01 / 2024:

1 - Quais são os horários com os vídeos mais populares?
  <div style="display: flex; flex-direction: row;">
   <img src="https://github.com/RafaelViniciusBrambillaAlves/Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure/assets/128416211/88acce68-30e9-49fa-83a0-b5c6181fdec8" width="400">
</div>

- O horário mais popular nesse dia é entre 14 e 16 horas

2 - Quais os canais com vídeos mais populares? 
  <div style="display: flex; flex-direction: row;">
   <img src="https://github.com/RafaelViniciusBrambillaAlves/Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure/assets/128416211/824c2059-bade-45ba-ad9e-f45292dbd68d" width="400">
</div>

- Nesse dia, o canal com mais vídeos populares foi a CazéTv

3 - Qual a melhor duração para o vídeo ser popular?
  <div style="display: flex; flex-direction: row;">
   <img src="https://github.com/RafaelViniciusBrambillaAlves/Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure/assets/128416211/7603d756-ac84-432e-b9b8-8e4235194324" width="400">
</div>

- Os vídeos mais populares tem menos de 15 minutos

4 - Quais são os canais com mais visualização?
  <div style="display: flex; flex-direction: row;">
   <img src="https://github.com/RafaelViniciusBrambillaAlves/Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure/assets/128416211/e97f8244-c8e6-4695-af20-959e4291e65f" width="400">
</div>


- Nesse dia, o canal com mais visualizações foi o 이지금 IU Official

5 - Quais são os números de visualização do vídeos mais populares?
  <div style="display: flex; flex-direction: row;">
   <img src="https://github.com/RafaelViniciusBrambillaAlves/Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure/assets/128416211/e4427086-127a-4b88-88e7-f4f3645ba5cb" width="400">
</div>

- Nesse dia a maioria dos vídeos populares tinham menos de 1M de visualizações


### Orquestração com Azure Data Factory
Toda a orquestração do fluxo de trabalho é realizada pelo Azure Data Factory. O arquivo etl_pipeline garantem a execução sequencial e automática dos notebooks em cada etapa do projeto, (extração, tratamento e visualização).

A imagem abaixo mostra o fluxo do trabalho
![image](https://github.com/RafaelViniciusBrambillaAlves/Extracao-e-Analise-de-Dados-da-API-do-YouTube-com-Azure/assets/128416211/ee08ed8e-48c7-4473-8336-34fa391b11d9)

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
