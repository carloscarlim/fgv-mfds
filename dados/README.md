# Dados da disciplina

| Arquivo | Fonte | Link | Extração | Observação |
|---|---|---|---|---|
| `anp_combustiveis_2026s1.csv.gz` | ANP – Série histórica de preços de combustíveis (combustíveis automotivos, 1º semestre de 2026) | [gov.br/anp](https://www.gov.br/anp/pt-br/centrais-de-conteudo/dados-abertos/serie-historica-de-precos-de-combustiveis) | 08/10/2026 | Recorte com 8 colunas (região, UF, município, produto, data, preço de venda, unidade, bandeira). Removidos endereço, CNPJ e nome do posto. 422.418 coletas |
| `olist_demo_clientes.csv.gz` | Olist – Brazilian E-Commerce Public Dataset (Kaggle) | [kaggle.com/datasets/olistbr/brazilian-ecommerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) | 08/10/2026 | Resumo por cliente (92.747 clientes, pedidos entregues de 2016 a 2018): UF, nº de pedidos, valor total, frete médio, recência, atraso médio e nota média. Licença: CC BY-NC-SA 4.0 [VERIFICAR na página do Kaggle] |
| `olist_pedidos.csv.gz`, `olist_itens.csv.gz`, `olist_clientes.csv.gz`, `olist_avaliacoes.csv.gz`, `olist_produtos.csv.gz` | Olist – Brazilian E-Commerce Public Dataset (Kaggle) | mesmo link acima | 08/10/2026 | Tabelas originais com colunas selecionadas: sem CEP, sem textos das avaliações e sem geolocalização. Nomes de colunas originais (inglês) |
| `cpgf_202608.csv.gz` | Portal da Transparência (CGU) – Cartão de Pagamento do Governo Federal, extrato de 08/2026 | [portaldatransparencia.gov.br/download-de-dados/cpgf](https://portal.transparencia.gov.br/download-de-dados/cpgf) | 08/10/2026 | 15.237 transações. **Minimização (LGPD):** removidos CPF e nome dos portadores e CPF e nome dos favorecidos pessoa física; mantidos órgão, unidade gestora, tipo de transação, data, valor e nome/CNPJ de favorecidos pessoa jurídica |
| `teste_ambiente.csv` | Fictício | – | – | Apenas para o teste de ambiente (NB00) |

Os recortes seguintes serão adicionados aula a aula, sempre com fonte, link e data de extração.
