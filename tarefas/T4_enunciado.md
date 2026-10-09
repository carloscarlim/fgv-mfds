# Tarefa 4 – Distribuições, outliers e correlação
**Métodos e Ferramentas de Data Science – FGV MBA** · Individual · Vale 7,5% da nota final

**Objetivo:** descrever a distribuição de uma variável de negócio, detectar valores fora do padrão, medir correlações e transformar os números numa regra de decisão.
A tarefa prepara a Aula 5 (inferência e comunicação) e o trabalho final.

**Prazo:** 23h59 da véspera da Aula 5. **Tempo estimado:** até 1h30.

**Como entregar**
1. Abra no Colab e clique em *Arquivo → Salvar uma cópia no Drive*.
2. Preencha sua matrícula e execute a célula que carrega **a sua amostra** (metade dos itens vendidos da Olist, sorteada pela matrícula, já com os dados do produto).
3. Responda Q1 a Q9 com código e escreva o texto Q10.
4. Execute o **verificador de formato**. Baixe o arquivo, renomeie para `T4_<sua matrícula>.ipynb` e envie no ECLASS.

**Definições (siga exatamente: a correção é automática)**
- Use a tabela `base` da sua amostra. A variável principal é o frete por item, `freight_value`.
- **Assimetria:** `.skew()` do pandas. **Percentil 90:** `.quantile(0.9)`.
- **Limite superior pela regra do IQR:** Q3 + 1,5 × (Q3 − Q1), com Q1 = `.quantile(0.25)` e Q3 = `.quantile(0.75)`.
- **Correlações:** `.corr()` do pandas entre `price` e `freight_value`, com `method="pearson"` e `method="spearman"`.
- **Q9:** agrupe por `product_category_name` (itens sem categoria ficam de fora) e considere só categorias com **pelo menos 100 itens** na sua amostra.
- Valores em R$ e assimetria com 2 casas; correlações com 3 casas.

**Regras**
- Você pode usar assistentes de IA para tirar dúvidas, mas o texto Q10 deve ser seu e citar números **da sua amostra**. Textos iguais entre alunos vão para revisão do professor. Máximo de 80 palavras.

**Leitura preparatória para a Aula 5:** ESCOVEDO, KALINOWSKI & MARQUES, *Introdução à estatística para ciência de dados* (Casa do Código, 2024), temas: correlação e noções de inferência (amostra, intervalo de confiança, teste de hipóteses).

**Rubrica (10 pontos)**

| Critério | Pontos | Insuficiente | Adequado | Excelente |
|---|---|---|---|---|
| Posição, dispersão e forma (Q1 a Q4) | 3,0 | Menos da metade correta | Metade ou mais correta | Todas corretas |
| Outliers e correlação (Q5 a Q9) | 4,5 | Menos da metade correta | Metade ou mais correta | Todas corretas |
| Regra de decisão (Q10) | 2,5 | Sem regra ou sem números | Regra com números **ou** limitação pertinente | Regra justificada com números da sua amostra **e** limitação pertinente |

## Perguntas
- **Q1.** Média do frete por item.
- **Q2.** Mediana do frete por item.
- **Q3.** Assimetria do frete.
- **Q4.** Percentil 90 do frete.
- **Q5.** Limite superior do frete pela regra do IQR.
- **Q6.** Quantos itens da sua amostra têm frete **acima** desse limite?
- **Q7.** Correlação de Pearson entre preço e frete.
- **Q8.** Correlação de Spearman entre preço e frete.
- **Q9.** Entre as categorias com pelo menos 100 itens na sua amostra, qual tem o **maior frete mediano**?
- **Q10.** Em até 80 palavras: que **regra** você proporia à diretoria para revisar fretes fora do padrão (cite números da sua amostra) e qual **limitação** ela tem?
