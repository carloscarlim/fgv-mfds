# Cheat sheet · Python e pandas para análise de dados
**Métodos e Ferramentas de Data Science · FGV MBA**

## Python em 6 peças
| Peça | Exemplo |
|---|---|
| Variável | `preco = 6.55` · `uf = "RJ"` |
| Comparação | `razao <= 0.70` → `True` ou `False` |
| Lista | `precos = [6.27, 6.54, 6.79]` · `precos[0]` · `len(precos)` · `sum(precos)` |
| Dicionário | `pedido = {"valor": 189.9, "uf": "MG"}` · `pedido["valor"]` |
| Decisão | `if atrasou:` ↵ `    print("acionar SAC")` (dois-pontos e 4 espaços) |
| Repetição e função | `for p in precos:` · `def margem(preco, custo): return (preco - custo) / preco * 100` |

## Ler e olhar
```python
import pandas as pd
df = pd.read_csv("arquivo.csv")            # ou uma URL; sep=";" e decimal="," para CSV brasileiro
df.shape            # (linhas, colunas)
df.head()           # primeiras linhas
df.info()           # tipos e não nulos
df.isna().sum()     # faltantes por coluna
df["coluna"].value_counts()    # frequência de cada categoria
df["coluna"].nunique()         # quantos valores distintos
```

## Limpar e transformar
```python
df = df.drop_duplicates()                                  # remove linhas idênticas
df["data"] = pd.to_datetime(df["data"])                    # texto → data
df["dias"] = (df["entrega"] - df["compra"]).dt.days        # diferença em dias
df["mes"] = df["data"].dt.to_period("M")                   # mês da data
df["cat"] = df["cat"].str.strip().str.lower()              # padroniza texto
df["cat"] = df["cat"].fillna("sem_categoria")              # preenche faltantes
df.loc[df["frete"] > 1000, "frete"] = df["frete"] / 100    # corrige valores numa condição
df["faixa"] = pd.cut(df["peso"], bins=[0, 500, 2000, 50000], labels=["leve", "médio", "pesado"])
```

## Filtrar e ordenar
```python
df[df["uf"] == "RJ"]                                   # uma condição
df[(df["status"] == "delivered") & df["entrega"].notna()]   # E: &   ·   OU: |
df[df["produto"].isin(["GASOLINA", "ETANOL"])]          # pertence a uma lista
df.sort_values("valor", ascending=False).head(10)      # 10 maiores
```

## Agrupar e juntar
```python
df.groupby("uf")["valor"].mean()                                   # média por grupo
df.groupby("uf").agg(n=("id", "count"), media=("valor", "mean"))   # vários resumos
pd.crosstab(df["atrasou"], df["nota"], normalize="index")          # tabela cruzada em %
a.merge(b, on="chave", how="left")                                  # como um PROCV
```
**Cuidado:** juntar com uma tabela "muitos" (itens, avaliações) multiplica linhas. Agregue antes de juntar.

## Descrever distribuições
```python
s = df["frete"]
s.mean(), s.median(), s.mode()[0]          # posição
s.std(), s.quantile(0.75) - s.quantile(0.25)   # dispersão: desvio padrão e IQR
s.quantile([0.9, 0.99])                    # percentis
s.skew(), s.kurt()                         # assimetria e curtose
q1, q3 = s.quantile([0.25, 0.75]); limite = q3 + 1.5 * (q3 - q1)   # regra do IQR
df[["preco", "frete"]].corr(method="spearman")   # ou method="pearson"
```

## Gráficos
```python
import seaborn as sns, matplotlib.pyplot as plt
sns.histplot(df["frete"], bins=50); plt.show()               # histograma (log_scale=True para caudas longas)
sns.boxplot(data=df, x="faixa", y="frete"); plt.show()       # box plot por grupo
sns.scatterplot(data=df, x="peso", y="frete"); plt.show()    # dispersão
sns.heatmap(df.corr(numeric_only=True), annot=True); plt.show()   # mapa de correlação
plt.title("Título que é a conclusão, não a descrição")
```

## Inferência em uma linha
```python
import numpy as np
from scipy import stats
ep = s.std() / np.sqrt(len(s)); ic = (s.mean() - 1.96 * ep, s.mean() + 1.96 * ep)   # IC de 95%
stats.ttest_ind(grupo_a, grupo_b, equal_var=False)      # diferença de médias: p-valor
```

## Erros mais comuns
| Mensagem | O que fazer |
|---|---|
| `NameError` | Execute as células anteriores (*Ambiente de execução → Executar anteriores*) |
| `KeyError: 'col'` | Confira o nome exato da coluna em `df.columns` |
| `SyntaxError` ou `IndentationError` | Dois-pontos no fim de `if`/`for`/`def`; 4 espaços dentro |
| `TypeError` com datas | Converta com `pd.to_datetime` antes de subtrair |
| Números dobrados depois do `merge` | Agregue a tabela "muitos" antes de juntar |
