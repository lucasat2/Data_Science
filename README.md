# 🐍 Jornada Python - Data Science

Este repositório contém meu progresso nos estudos de Python, com foco em manipulação de dados.


## 📂 Estrutura do Projeto


### ✈️ Projeto: Análise de Voos
*Aplicação prática em um conjunto de dados do mundo real.*

* [Projeto](Projeto_Analise_voo/Projeto_Analise_dados_voo.ipynb)


## 🎯 Checklist de Competências (O que já domino)

Habilidades técnicas que desenvolvi e documentei nestes cadernos, organizadas por categoria:

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