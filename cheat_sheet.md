# 📖 Dicionário de Comandos e Funções

Neste arquivo, listo os principais comandos que aprendi, separados por tema para facilitar a consulta rápida.

---

## 📥 Leitura e Escrita de Dados
* `pd.read_csv('arquivo.csv')` - Abre arquivos CSV.
* `pd.read_excel('arquivo.xlsx')` - Abre planilhas Excel.
* `df.to_csv('nome.csv')` - Salva o DataFrame no computador.

## 🔍 Informações do Data Frame
* `df.head()` - Mostra as 5 primeiras linhas.
* `df.info()` - Mostra os tipos de dados e valores nulos.
* `df.describe()` - Gera o resumo estatístico (média, min, max).
* `df.describe(include="all")` - Pega valores não numéricos (unique, top, freq).
* `df.shape` - Mostra o número de linhas e colunas.
* `df.dtypes` - Mostra os tipos de dados de cada coluna.

## 🧹 Limpeza e Transformação
* `df.isna().sum()` - Conta quantos valores vazios existem.
* `df.dropna()` - Remove linhas com valores vazios.
* `df.fillna(0)` - Preenche valores vazios com zero.
* `df.drop_duplicates()` - Remove linhas repetidas.
* `df.duplicated().sum()` - Conta o total de linhas duplicadas.

## ✂️ Filtros e Seleção
* `df['coluna']` - Seleciona uma única coluna (Series).
* `df[['col1', 'col2']]` - Seleciona várias colunas (DataFrame).
* `df.iloc[linhas, colunas]` - Seleciona dados por **posição numérica** (ex: `df.iloc[0:3, 0:2]`).
* `df.loc[linhas, colunas]` - Seleciona dados por **rótulo/nome** ou **condição booleana**.
* `df[df['valor'] > 100]` - Filtra linhas com base em uma condição simples.
* `(cond1) & (cond2)` - Operador **E** (ambas as condições verdadeiras).
* `(cond1) | (cond2)` - Operador **OU** (pelo menos uma condição verdadeira).
* `~(condicao)` - Operador **NÃO** (inverte a condição).
* `df.sort_values('coluna', ascending=False)` - Ordena os dados (ex: do maior para o menor).

## 🧮 Agrupamento e Estatística
* `df.groupby('coluna')` - Agrupa os dados por categoria.
* `.agg({'col': 'sum'})` - Faz cálculos (soma, média) no grupo.
* `df["coluna"].unique()` - Lista os valores únicos diferentes.
* `df["coluna"].nunique()` - Conta o número de categorias únicas.
* `df["coluna"].value_counts()` - Conta a frequência de cada item.
* `df["coluna"].value_counts(normalize=True)` - Mostra as frequências em porcentagem/proporção.
* `.nlargest(n, 'col')` - Retorna os N maiores valores.
* `df["col"].quantile(0.25)` - Calcula o 1º Quartil (25%).
* `df["col"].quantile(0.50)` - Calcula a Mediana (50%).
* `df["col"].quantile(0.75)` - Calcula o 3º Quartil (75%).
* `df["col"].min()`, `df["col"].max()`, `df["col"].mean()` - Mínimo, máximo e média específicos.

## 📈 Visualização (Gráficos)
* `df.plot(kind='bar')` - Gráfico de barras.
* `df.plot(kind='hist', bins=30)` - Histograma.
* `plt.title('Texto')` - Define o título do gráfico.

---

## 🚨 Conceitos Importantes
* **Outliers** - Valores muito fora da curva padrão. Podem ser identificados visualmente ou via técnica de IQR (Q3 - Q1).
* **Parênteses em Filtros** - Sempre use `()` ao combinar condições com `&` ou `|` para evitar erros de prioridade no Python.
