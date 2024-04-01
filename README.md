# dashbord_python_pandas_jupyter
Dasboard Python: Biblioteca Pandas y Jupyter
# Dasboard Python: Biblioteca Pandas y Jupyter

Tenemos 1 base de datos con información de clientes, tanto clientes actuales como clientes que han cancelado su tarjeta

Descargar la base de datos: Botón de la página

Referência: https://www.kaggle.com/sakshigoyal7/credit-card-customers

Construir uma análise para identificar o motivo de cancelamento
  - Identificar qual o motivo ou os principais motivos dos clientes estarem cancelando o cartão de crédito

Construir uma análise para identificar o motivo de cancelamento
  - Identificar qual o motivo ou os principais motivos dos clientes estarem cancelando o cartão de crédito

Construir uma análise para identificar o motivo de cancelamento
  - Identificar qual o motivo ou os principais motivos dos clientes estarem cancelando o cartão de crédito

import pandas as pd

tabela = pd.read_csv("/content/drive/MyDrive/Minicurso Analise de Dados/ClientesBanco.csv", encoding="latin1")
tabela = tabela.drop("CLIENTNUM", axis=1)
display(tabela)

# Agora vamos tratar valores vazios e exibir um resumo das colunas da base de dados

tabela = tabela.dropna()
display(tabela.info())

display(tabela.describe().round(1))

# Vamos avaliar como está a divisão entre Clientes x Cancelados

qtde_categoria = tabela["Categoria"].value_counts()
display(qtde_categoria)

qtde_categoria_perc = tabela["Categoria"].value_counts(normalize=True)
display(qtde_categoria_perc)

# Temos vários formas de descobrir o motivo de cancelamento
  - Podemos olhar a comparação entre Clientes e Cancelados em cada uma das colunas da nossa base de dados, para ver se essa informação traz algum insight novo para a gente

import plotly.express as px

for coluna in tabela:
  grafico = px.histogram(tabela, x=coluna, color="Categoria")
  grafico.show()

# Informações retiradas da análise

- Me parece que quanto mais produtos contratados um cliente tem, menor a chance dele cancelar
- E quanto mais transações e quanto maior o valor de transação, menor a chance dele cancelar
- Quanto maior a quantidade de contatos que a pessoa teve que fazer, maior a chance dela cancelar
