# 📊 Data Engineering Pipeline – Arquitetura Bronze, Silver e Gold

Este projeto demonstra a construção de um **pipeline de engenharia de dados utilizando Python**, aplicando boas práticas de **Data Lakehouse e modelagem dimensional**.

O objetivo é transformar dados brutos de vendas em um **modelo analítico estruturado**, preparado para consumo por ferramentas de BI e análises avançadas.

---

# 🚀 Visão Geral da Solução

O pipeline segue uma arquitetura em camadas comum em projetos de engenharia de dados:

Bronze → Silver → Gold

**Fluxo do processamento**

1. **Bronze Layer**
   - Ingestão de dados brutos em formato CSV.

2. **Silver Layer**
   - Limpeza e transformação dos dados
   - Normalização de colunas
   - Tratamento de datas e campos textuais
   - Criação de datasets intermediários
   - Conversão para formato **Parquet**

3. **Gold Layer**
   - Construção de **modelo dimensional**
   - Criação de **tabelas dimensão**
   - Criação da **tabela fato de vendas**
   - Geração de **surrogate keys**
   - Particionamento da tabela fato por **Ano e Mês**

---

# 🏗 Arquitetura do Pipeline

CSV (Raw Data)
│
▼
BRONZE
Dados brutos de vendas
│
▼
SILVER
Limpeza e transformação
Normalização de dados
Conversão para Parquet
│
▼
GOLD
Modelo dimensional
Star Schema
Tabela fato + dimensões
Particionamento por data


---

# 🧱 Modelagem Dimensional

A camada Gold implementa um **Star Schema** com as seguintes tabelas:

### Tabela Fato
- **fato_vendas**
  - Data
  - Produto
  - Categoria
  - Segmento
  - Cliente
  - Cidade
  - Unidades
  - Custo Unitário
  - Preço Unitário

### Tabelas Dimensão

- d_produto
- d_categoria
- d_segmento
- d_fabricante
- d_cliente
- d_cidade
- d_estado
- d_regiao
- d_pais

Cada dimensão possui **Surrogate Key (SK)** gerada no processo ETL.

---

# 🔄 Principais Transformações

Durante o processamento foram aplicadas diversas transformações:

### Tratamento de dados
- Separação de **Email e Nome**
- Limpeza de caracteres
- Padronização de campos textuais
- Conversão e formatação de datas

### Normalização geográfica
- Separação de:
  - Cidade
  - Estado
  - Região
  - País

### Engenharia de dados
- Remoção de colunas desnecessárias
- Criação de dimensões por **deduplicação**
- Conversão de datasets para **Parquet**
- Particionamento da tabela fato

---

# ⚡ Particionamento de Dados

A tabela fato foi particionada por:

- **Ano**
- **Mês**

Isso melhora significativamente:

- Performance de leitura
- Escalabilidade
- Processamento analítico

Estrutura gerada:

GOLD/
fato_vendas_particionado/
Ano=2023/
Mes=01/
Mes=02/


---

# 🛠 Tecnologias Utilizadas

- **Python**
- **Pandas**
- **PyArrow**
- **Parquet**
- **Jupyter Notebook / VS Code**
- **Modelagem Dimensional**

Bibliotecas principais:

pandas
pyarrow
pyodbc
pillow


---

# 📂 Estrutura do Projeto

data-engineering-pipeline/

│
├── BRONZE/
│ └── vendas.csv
│
├── SILVER/
│ └── datasets transformados
│
├── GOLD/
│ ├── dimensoes
│ └── fato_vendas_particionado
│
├── notebooks
│ └── pipeline_dados.ipynb
│
└── README.md


---

# 📈 Possíveis Evoluções do Projeto

Este pipeline pode ser facilmente evoluído para cenários reais de produção:

- Orquestração com **Airflow ou Prefect**
- Processamento distribuído com **Spark**
- Ingestão automatizada via **APIs ou streaming**
- Armazenamento em **Data Lake (Azure / AWS / GCP)**
- Camada semântica para **Power BI ou Tableau**

---

# 🎯 Competências Demonstradas

Este projeto demonstra habilidades importantes para **Engenharia de Dados**:

- Construção de pipelines de dados
- Arquitetura Bronze / Silver / Gold
- Modelagem dimensional
- Transformação de dados com Python
- Otimização com Parquet e particionamento
- Estruturação de datasets analíticos

---

# 👩‍💻 Autor

Juliana Ferreira  
