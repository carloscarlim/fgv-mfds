# Tarefa 3 – Análise descritiva com pandas
**Métodos e Ferramentas de Data Science – FGV MBA** · Individual · Vale 7,5% da nota final

**Objetivo:** usar o pandas para carregar, filtrar, juntar, agrupar e resumir dados reais, e transformar o resultado numa mensagem para a diretoria.
A tarefa prepara a Aula 4, em que vamos olhar distribuições, outliers e correlação na mesma base.

**Prazo:** 23h59 da véspera da Aula 4. **Tempo estimado:** até 1h30.

**Como entregar**
1. Abra no Colab e clique em *Arquivo → Salvar uma cópia no Drive*.
2. Preencha sua matrícula e execute a célula que carrega **a sua amostra** (metade dos pedidos da Olist, sorteada pela matrícula).
3. Responda Q1 a Q9 com código e escreva o texto Q10.
4. Execute o **verificador de formato**. Baixe o arquivo (*Arquivo → Fazer download → .ipynb*), renomeie para `T3_<sua matrícula>.ipynb` e envie no ECLASS.

**Definições (siga exatamente: a correção é automática)**
- **Pedido entregue:** `order_status == "delivered"` **e** `order_delivered_customer_date` não nula.
- **Dias de entrega:** `(order_delivered_customer_date − order_purchase_timestamp).dt.days`, depois de converter as datas com `pd.to_datetime`.
- **Atrasou:** `order_delivered_customer_date > order_estimated_delivery_date`.
- **Nota de um pedido:** média de `review_score` por `order_id` (agrupe as avaliações **antes** de juntar).
- **Porcentagens** de 0 a 100, com 2 casas (ex.: `8.13`). Dias e notas com 2 casas.

**Regras**
- Use apenas a sua amostra (variável `pedidos`), exceto onde a pergunta disser o contrário.
- Você pode usar assistentes de IA para tirar dúvidas, mas o texto Q10 deve ser seu e citar números **da sua amostra**. Textos iguais entre alunos vão para revisão do professor. Máximo de 80 palavras.

**Leitura preparatória para a Aula 4:** ESCOVEDO, KALINOWSKI & MARQUES, *Introdução à estatística para ciência de dados* (Casa do Código, 2024), tema: estatística descritiva, medidas de posição e dispersão.

**Rubrica (10 pontos)**

| Critério | Pontos | Insuficiente | Adequado | Excelente |
|---|---|---|---|---|
| Carregar, filtrar e resumir (Q1 a Q5) | 3,5 | Menos da metade correta | Metade ou mais correta | Todas corretas |
| Agrupar e juntar tabelas (Q6 a Q9) | 4,0 | Menos da metade correta | Metade ou mais correta | Todas corretas |
| Mensagem à diretoria (Q10) | 2,5 | Sem achado ou sem números | Achado com números **ou** limitação pertinente | Achado com números da sua amostra **e** limitação pertinente |

## Perguntas
- **Q1.** Quantos pedidos há na sua amostra?
- **Q2.** Que porcentagem dos pedidos da sua amostra tem status `delivered`?
- **Q3.** Prazo médio de entrega (dias) dos pedidos entregues.
- **Q4.** Prazo mediano de entrega (dias) dos pedidos entregues.
- **Q5.** Porcentagem de pedidos entregues que atrasaram.
- **Q6.** Entre os estados do cliente (`customer_state`) com **pelo menos 200 pedidos entregues** na sua amostra, qual tem a **maior porcentagem de atraso**? (sigla, ex.: `"RJ"`)
- **Q7.** Nota média dos pedidos entregues **atrasados** (considere só os pedidos que têm nota).
- **Q8.** Nota média dos pedidos entregues **no prazo**.
- **Q9.** Considerando os itens dos pedidos da sua amostra (qualquer status), qual categoria (`product_category_name`) teve o **maior faturamento** (soma de `price`)?
- **Q10.** Em até 80 palavras, escreva ao diretor comercial: o principal achado, com números da sua amostra, e **uma** limitação dos dados que ele precisa conhecer.
