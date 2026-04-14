# 🐍 Jornada Python - Análise de Dados

Este repositório contém meu progresso nos estudos de Python, com foco em manipulação de dados usando a biblioteca Pandas.

---

## 📂 Estrutura do Projeto

### 1. 🧪 Introdução ao Pandas
*Conteúdos fundamentais para entender a estrutura e manipulação de tabelas.*

* [Teoria](1-introducao_pandas/Revisional_Pandas.ipynb) - Visão geral do Pandas.
* [Operações em DataFrames](introducao_pandas/operacoes_dataframe.ipynb) - Cálculos e manipulações básicas.
* [Agrupamento e Agregação](introducao_pandas/Agrupamento_e_Agregacao.ipynb) - Como resumir dados com `groupby`.
* [Limpeza de Dados](introducao_pandas/Limpeza__de_dados.ipynb) - Tratamento de nulos e duplicados.

---

### ✈️ Projeto: Análise de Voos
*Aplicação prática em um conjunto de dados do mundo real.*

* [Leitura de Dados](projeto_analise_voo/02_leitura_dados_mundo_real.ipynb) - Como carregar diferentes formatos.
* [Revisão e Tipos](projeto_analise_voo/1-revisão_dataframe.ipynb) - Verificação de `dtypes`.
* [Datas e Índices](projeto_analise_voo/2-index_e_datetime.ipynb) - Manipulação de colunas temporais.
* [Análise Exploratória (EDA)](projeto_analise_voo/4-EDA.ipynb) - Descoberta de insights e padrões.
* **[PROJETO FINAL](projeto_analise_voo/Projeto_Pandas_Analise_dados_voo.ipynb)** - Relatório consolidado com gráficos.



## 🎯 Checklist de Competências (O que já domino)

Abaixo estão as habilidades técnicas que desenvolvi e documentei nestes cadernos, organizadas por categoria:

### 📥 Importação e Exportação
- [x] Leitura de CSVs com diferentes separadores e encodings (`sep`, `encoding`).
- [x] Otimização de leitura com `usecols` e `nrows`.
- [x] Leitura de arquivos Excel com múltiplas abas (`sheet_name`).
- [x] Salvamento de progresso em novos arquivos CSV/Excel.

### 🧹 Limpeza e Preparação (Data Wrangling)
- [x] Identificação e tratamento de valores nulos (`isna`, `dropna`, `fillna`).
- [x] Remoção de dados duplicados (`drop_duplicates`).
- [x] Conversão de tipos de dados (`astype`, `to_numeric`).
- [x] Manipulação avançada de datas (`to_datetime`).
- [x] Renomeação de colunas e ajuste de índices (`rename`, `set_index`, `reset_index`).

### 🔍 Filtros e Seleção
- [x] Filtros condicionais simples e compostos (ex: Voos > 2000km).
- [x] Seleção inteligente de dados com `.loc` e `.iloc`.
- [x] Uso de `.copy()` para evitar o `SettingWithCopyWarning`.

### 📊 Análise e Agregação
- [x] Resumos estatísticos com `describe()`.
- [x] Contagem de valores categóricos (`value_counts`, `unique`).
- [x] Agrupamentos complexos com `groupby` e múltiplas agregações (`agg`).
- [x] Identificação de "Top N" valores usando `nlargest`.

### 📈 Visualização de Dados
- [x] Criação de gráficos de barras e histogramas.
- [x] Ajustes estéticos (títulos, legendas, rotação de eixos).
- [x] Aplicação de escala logarítmica para dados discrepantes.