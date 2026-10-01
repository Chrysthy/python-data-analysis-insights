# Snippets Úteis de Python

Referência rápida de comandos úteis de Python, pandas e análise de dados.

---

## Read a CSV file

Lê um arquivo CSV e transforma os dados em um DataFrame do pandas.

```python
import pandas as pd

tabela = pd.read_csv("../data/cancelamentos.csv")
```

---

## Check current working directory

Mostra o diretório atual em que o Python está executando o código.

Isso é útil quando aparece algum erro de caminho ou quando o Python não consegue encontrar um arquivo.

```python
import os

print(os.getcwd())
```

---

## Preview the dataset

Mostra as primeiras linhas do DataFrame.

```python
tabela.head()
```

Para visualizar as últimas linhas:

```python
tabela.tail()
```

---

## Check dataset information

Mostra informações gerais sobre o DataFrame.

```python
tabela.info()
```

Pode ser usado para verificar:

- nomes das colunas
- quantidade de linhas
- tipos de dados
- quantidade de valores não nulos
- possíveis valores ausentes

---

## Check dataset dimensions

Mostra a quantidade de linhas e colunas do DataFrame.

```python
tabela.shape
```

O resultado segue este formato:

```text
(linhas, colunas)
```

Exemplo:

```text
(800000, 18)
```

---

## Remove columns

Para remover uma única coluna:

```python
tabela = tabela.drop(columns="CustomerID")
```

Para remover várias colunas:

```python
tabela = tabela.drop(columns=["CustomerID", "Age", "Gender"])
```

Quando mais de uma coluna for removida, os nomes devem ser colocados dentro de uma lista.

---

## Check missing values

Verifica quantos valores ausentes existem em cada coluna.

```python
tabela.isnull().sum()
```

Também pode ser usado:

```python
tabela.isna().sum()
```

Os dois comandos possuem função semelhante nesse caso.

---

## Remove missing values

Remove linhas que possuem valores ausentes.

```python
tabela = tabela.dropna()
```

Também é possível remover valores ausentes considerando apenas colunas específicas:

```python
tabela = tabela.dropna(subset=["Age"])
```

---

## Check duplicated rows

Verifica a quantidade de linhas duplicadas.

```python
tabela.duplicated().sum()
```

Para remover as duplicatas:

```python
tabela = tabela.drop_duplicates()
```

---

## Count values in a column

Conta quantas vezes cada valor aparece em uma coluna.

```python
tabela["Cancelou"].value_counts()
```

---

## Show values as percentage

Mostra a proporção de cada valor.

```python
tabela["Cancelou"].value_counts(normalize=True)
```

Para transformar em porcentagem:

```python
tabela["Cancelou"].value_counts(normalize=True) * 100
```

---

## Filter data

Filtra o DataFrame usando uma condição.

```python
tabela[tabela["Cancelou"] == 1]
```

Com mais de uma condição:

```python
tabela[
    (tabela["Cancelou"] == 1) &
    (tabela["Idade"] > 30)
]
```

Operadores úteis:

```text
==  igual
!=  diferente
>   maior
<   menor
>=  maior ou igual
<=  menor ou igual
```

Para combinar condições:

```text
&   AND
|   OR
```

---

## Group data

Agrupa os dados com base em uma coluna.

```python
tabela.groupby("TipoAssinatura")["Cancelou"].mean()
```

Pode ser útil para comparar o comportamento de diferentes grupos de clientes.

Por exemplo, verificar se determinado tipo de assinatura possui uma taxa maior de cancelamento.

---

## Sort values

Ordena os dados em ordem crescente.

```python
tabela.sort_values("Idade")
```

Para ordem decrescente:

```python
tabela.sort_values("Idade", ascending=False)
```

---

## Select a column

Seleciona apenas uma coluna do DataFrame.

```python
tabela["Age"]
```

---

## Select multiple columns

Seleciona várias colunas.

```python
tabela[["Age", "Gender", "Cancelou"]]
```

Quando mais de uma coluna é selecionada, os nomes devem ficar dentro de uma lista.

---

## Check column names

Mostra todos os nomes das colunas existentes no DataFrame.

```python
tabela.columns
```

Pode ser útil antes de usar comandos como `drop()`, filtros ou `groupby()`.

---

## Rename columns

Renomeia uma ou mais colunas.

```python
tabela = tabela.rename(columns={
    "CustomerID": "Customer_ID",
    "Age": "Customer_Age"
})
```

---

## Check unique values

Mostra quais valores diferentes existem em uma coluna.

```python
tabela["ContractType"].unique()
```

Para saber quantos valores únicos existem:

```python
tabela["ContractType"].nunique()
```

---

## Basic statistical summary

Mostra informações estatísticas das colunas numéricas.

```python
tabela.describe()
```

Pode mostrar informações como:

- média
- desvio padrão
- valor mínimo
- valor máximo
- mediana
- quartis

---

## Check data types

Mostra o tipo de dado de cada coluna.

```python
tabela.dtypes
```

Exemplos de tipos:

```text
int64
float64
object
bool
datetime64
```

---

## Change data type

Altera o tipo de dado de uma coluna.

```python
tabela["Age"] = tabela["Age"].astype(int)
```

Outro exemplo:

```python
tabela["Cancelou"] = tabela["Cancelou"].astype(bool)
```

---

## Reset index

Reorganiza o índice do DataFrame.

```python
tabela = tabela.reset_index(drop=True)
```

O `drop=True` evita que o índice antigo seja criado como uma nova coluna.

---

## Save DataFrame as CSV

Salva o DataFrame em um novo arquivo CSV.

```python
tabela.to_csv("../data/dados_tratados.csv", index=False)
```

O `index=False` evita que o índice do pandas seja salvo como uma coluna no arquivo.

---

## Read Excel file

Lê um arquivo Excel.

```python
tabela = pd.read_excel("../data/dados.xlsx")
```

---

## Save DataFrame as Excel

Salva o DataFrame como arquivo Excel.

```python
tabela.to_excel("../data/dados_tratados.xlsx", index=False)
```

Para trabalhar com arquivos Excel, pode ser necessário ter `openpyxl` instalado.

---

## Create a simple chart with Plotly

Exemplo de gráfico usando Plotly.

```python
import plotly.express as px

grafico = px.histogram(
    tabela,
    x="Age",
    color="Cancelou"
)

grafico.show()
```

Plotly pode ser usado para criar gráficos interativos durante a análise dos dados.

---

## Extract PDF tables with tabula-py

A biblioteca `tabula-py` pode ser usada para extrair tabelas de arquivos PDF.

Instalação:

```bash
pip install tabula-py
```

Exemplo:

```python
import tabula

tabelas = tabula.read_pdf(
    "arquivo.pdf",
    pages="all"
)
```

O resultado pode ser trabalhado como DataFrame para análise com pandas.

`tabula-py` é útil principalmente quando os dados estão em tabelas dentro de PDFs, em vez de arquivos CSV ou Excel.

---

## Useful data sources

Algumas plataformas podem ser utilizadas para encontrar datasets para estudos e projetos de portfólio.

### Kaggle

O Kaggle possui diversos datasets públicos que podem ser utilizados em projetos de:

- Data Analysis
- Data Science
- Machine Learning
- Data Visualization
- Python
- SQL

Os datasets podem ser encontrados em:

```text
https://www.kaggle.com/datasets
```

---

## Common file formats

Formatos comuns usados em projetos de análise de dados:

```text
.csv   -> Comma-Separated Values
.xlsx  -> Excel
.json  -> JavaScript Object Notation
.pdf   -> Portable Document Format
```

Algumas bibliotecas comuns para trabalhar com esses formatos:

```text
CSV / Excel -> pandas
Excel       -> openpyxl
PDF tables  -> tabula-py
JSON        -> pandas / json
```