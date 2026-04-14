# 📖 Dicionário de Comandos e Funções

Neste arquivo, listo os principais comandos que aprendi, separados por tema para facilitar a consulta rápida.

---

## 📥 Leitura e Escrita de Dados
* `pd.read_csv('arquivo.csv')` - Abre arquivos CSV.
* `pd.read_excel('arquivo.xlsx')` - Abre planilhas Excel.
* `df.to_csv('nome.csv')` - Salva o DataFrame no computador.

## 🔍 Exploração Inicial
* `df.head()` - Mostra as 5 primeiras linhas.
* `df.info()` - Mostra os tipos de dados e valores nulos.
* `df.describe()` - Gera o resumo estatístico (média, min, max).
* `df.shape` - Mostra o número de linhas e colunas.

## 🧹 Limpeza e Transformação
* `df.isna().sum()` - Conta quantos valores vazios existem.
* `df.dropna()` - Remove linhas com valores vazios.
* `df.fillna(0)` - Preenche valores vazios com zero.
* `df.drop_duplicates()` - Remove linhas repetidas.

## ✂️ Filtros e Seleção
* `df['coluna']` - Seleciona uma coluna.
* `df.loc[linhas, colunas]` - Seleciona dados por nome.
* `df[df['valor'] > 100]` - Filtra linhas com base em uma condição.

## 🧮 Agrupamento e Estatística
* `df.groupby('coluna')` - Agrupa os dados por categoria.
* `.agg({'col': 'sum'})` - Faz cálculos (soma, média) no grupo.
* `.value_counts()` - Conta quantas vezes cada item aparece.
* `.nlargest(n, 'col')` - Retorna os N maiores valores.

## 📈 Visualização (Gráficos)
* `df.plot(kind='bar')` - Gráfico de barras.
* `df.plot(kind='hist', bins=30)` - Histograma.
* `plt.title('Texto')` - Define o título do gráfico.