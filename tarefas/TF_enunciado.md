# Trabalho Final – Análise exploratória para a diretoria
**Métodos e Ferramentas de Data Science – FGV MBA** · Individual · **70% da nota final**

## a) O desafio

Você é o analista de dados de um e-commerce. A sua diretoria tem uma dor de negócio e pediu uma análise que a ajude a decidir.

Cada aluno recebe:
- **uma base individual**: 20% dos pedidos da Olist (e-commerce brasileiro, 2016–2018), sorteados pela sua matrícula (seu nome de usuário do ECLASS), em três tabelas (`pedidos`, `itens`, `avaliacoes`). Como toda base real, ela tem **problemas de qualidade** que você precisa encontrar, entender e tratar;
- **um cartão de cenário**: quem é a sua diretoria, qual a dor dela e uma métrica obrigatória.

O notebook-modelo `tarefas/TF_trabalho_final.ipynb` carrega a sua base e mostra o seu cartão. Você vai:
1. formular uma **pergunta de negócio** a partir do cartão;
2. **descrever e tratar** a base, documentando cada decisão;
3. **criar variáveis** a partir de datas, faixas e combinações de colunas;
4. fazer a **análise exploratória**: distribuições, outliers, correlação, comparação de grupos e intervalo de confiança;
5. responder às **perguntas verificáveis** (F1 a F17);
6. montar **um slide executivo** para a diretoria;
7. gravar um **vídeo de até 8 minutos** respondendo a perguntas feitas só para você, a partir do seu notebook.

As **regras de negócio** apresentadas nas aulas valem para o trabalho. Se faltar a uma aula, assista à gravação.

## b) Marcos e prazos

Os marcos são **obrigatórios e não valem nota**. Eles geram uma devolutiva automática para você melhorar antes da entrega final e fazem parte do registro do seu processo. Entregas finais sem marcos são revisadas pelo professor.

| Marco | O que entregar (no mesmo notebook, com `ETAPA` ajustada) | Prazo |
|---|---|---|
| Marco 1 | Pergunta de negócio, técnica, dados necessários e medida de sucesso (`MARCO1`) | 23h59 da véspera da Aula 3 |
| Marco 2 | Base inspecionada e dicionário de dados com as 12 colunas (`DICIONARIO`) | 23h59 da véspera da Aula 4 |
| Marco 3 | Limpeza documentada e as respostas que já conseguir calcular | 23h59 da véspera da Aula 5 |
| **Entrega final** | Notebook completo (F1 a F17 e declaração de uso de IA) **e** o slide executivo | **23h59 do 7º dia depois da Aula 5** |
| Perguntas do vídeo | Você recebe por e-mail as suas perguntas personalizadas | Até 24 h depois do prazo da entrega final |
| **Vídeo** | Até 8 minutos | **72 h depois de receber as perguntas** |

**Como enviar (ECLASS):** notebook `TF_<seu usuário>.ipynb`; slide `TF_<seu usuário>.pdf` ou `TF_<seu usuário>.pptx`; vídeo `<seu usuário>.mp4`. Se o vídeo passar do limite de tamanho do ECLASS, envie um link do Google Drive compartilhado só com ext.carlos.pinto@prof.fgv.br.

## c) Estrutura do entregável

**1. Notebook** (o modelo já traz as seções):
- seções 0 e 1: matrícula, etapa, base e cartão;
- seção 2: Marco 1;
- seção 3: inspeção e dicionário de dados;
- seção 4: limpeza, novas variáveis e análise, com **células de texto explicando cada decisão e cada achado**;
- seção 5: respostas verificáveis F1 a F17;
- seção 6: orientações do slide;
- seção 7: declaração de uso de IA;
- seção 8: verificador (execute antes de cada envio).

O notebook precisa **rodar do início ao fim sem erro** (*Ambiente de execução → Reiniciar e executar tudo*).

**2. Definições das respostas verificáveis** (siga exatamente: a correção é automática)

*Preparação dos dados*

| Item | Definição |
|---|---|
| F1 | Linhas de `pedidos` idênticas em todas as colunas, removidas (mantém uma de cada). Todos os itens abaixo usam a tabela de pedidos já sem duplicatas |
| F2 | Entre os pedidos com `order_status == "delivered"` e data de entrega não nula: prazo `(entrega − compra).dt.days` negativo ou acima de 365 dias. Esses pedidos ficam fora das análises de prazo e atraso. Os demais são os **pedidos entregues válidos** |
| F3 | Número de fretes corrigidos pela regra de negócio da Aula 4 |
| F4 | Número de itens com frete igual a zero na base tratada (aplique a regra de negócio da Aula 3) |
| F5 | Linhas de `itens` cuja categoria muda ao padronizar com `.str.strip().str.lower()` |
| F13 | Pedidos **sem data de entrega**, separados em dois grupos: os que **não** têm status `delivered` e os que **têm** status `delivered`. No notebook, explique qual dos dois grupos é um faltante esperado e qual é um problema de qualidade |

*Análise exploratória e novas variáveis (base tratada)*

| Item | Definição |
|---|---|
| F6 e F7 | Prazo mediano (dias) e porcentagem de atraso (`entrega > data estimada`) dos pedidos entregues válidos |
| F8 | Mediana e média de `freight_value` em todos os itens da base tratada |
| F9 | Correlação de Spearman entre `freight_value` e `product_weight_g`, nos itens com peso maior que zero |
| F10 | Nota de cada pedido = média de `review_score` por `order_id`. Diferença: nota média dos atrasados − nota média dos no prazo (pedidos entregues válidos com nota). Intervalo de confiança de 95%: diferença ± 1,96 × √(s²₁/n₁ + s²₂/n₂) |
| F11 | Porcentagem dos pedidos entregues válidos **sem nota**, entre os atrasados e entre os no prazo |
| F12 | A métrica do seu cartão de cenário |
| F14 | Crie a variável "dia da semana da compra". Porcentagem de atraso dos pedidos entregues válidos **comprados no sábado ou no domingo** |
| F15 | Crie a variável "faixa de peso" com `pd.cut(product_weight_g, bins=[0, 500, 2000, 10000, float("inf")])`. Frete mediano da faixa **acima de 10 kg** |
| F16 | Crie a variável "experiência ruim" = atrasou **ou** nota menor ou igual a 2 (pedido sem nota conta só pelo atraso). Porcentagem de pedidos entregues válidos com experiência ruim |
| F17 | Crie a variável "mês da compra" (`AAAA-MM`). Entre as combinações estado do cliente × mês da compra, a de **maior porcentagem de atraso** (em empate, a de mais pedidos; persistindo, ordem alfabética do estado e do mês), no formato `"UF\|AAAA-MM"`, **e** quantos pedidos entregues válidos ela tem. Você vai precisar explicar esse resultado no vídeo |

Porcentagens de 0 a 100 com 2 casas; dias, reais e notas com 2 casas; correlação com 3 casas.

**3. Slide executivo** (um único slide, a partir do modelo `tarefas/TF_modelo_slide.pptx`), para a diretoria do seu cartão:
- **título** com o achado principal, em uma frase, com um número;
- a **pergunta de negócio**;
- **3 insights** com números da sua base, incluindo a métrica do cenário (F12);
- **3 ações recomendadas**, cada uma com uma condição verificável (meta, prazo ou indicador);
- **1 limitação** e a incerteza dos números;
- **1 gráfico** feito por você no notebook, com um título que seja a conclusão.

## d) O vídeo

- Até **8 minutos**. Acima de 8 minutos, há desconto de 2 pontos.
- **Câmera ligada** num canto da tela e o **seu notebook aberto** na tela durante todo o vídeo.
- Responda, na ordem, às perguntas que você receber:
  - três perguntas sobre as **suas** decisões e números;
  - **uma alteração para executar ao vivo** no notebook (por exemplo, recalcular algo com outro parâmetro e dizer o resultado);
  - uma pergunta sobre a **incerteza** dos seus resultados;
  - **um minuto de recomendação** para a diretoria.
- Não é preciso editar nem ter produção caprichada: vale o raciocínio. Você pode gravar com o Google Meet, Zoom, Teams ou o gravador de tela do computador.
- **Avaliação:** o vídeo é assistido e avaliado pelo professor, um a um.
- **Privacidade:** o vídeo é usado só para a avaliação, fica numa pasta restrita e é apagado ao fim do prazo de revisão de notas.

## e) Rubrica (70 pontos)

| Componente | Critério | Pontos | Competências |
|---|---|---|---|
| **Notebook (25)** | Preparação dos dados: F1 a F5 e F13 corretos | 10 | C2, C4 |
| | Rigor da EDA e novas variáveis: F6 a F12 e F14 a F17 corretos | 10 | C2, C3 |
| | Qualidade do código: roda do início ao fim sem erro | 3 | C4 |
| | Decisões de limpeza e achados documentados em texto | 2 | C2 |
| **Slide (20)** | Pergunta de negócio ligada ao cartão e título com o achado | 3 | C1 |
| | 3 insights com números corretos da sua base, incluindo F12 | 6 | C2, C3 |
| | 3 ações acionáveis, cada uma com condição verificável | 5 | C1 |
| | Limitação e incerteza | 4 | C2 |
| | Clareza: um único slide, legível, gráfico com título-mensagem | 2 | C2 |
| **Vídeo (25)** | Respostas às três perguntas sobre o seu trabalho (4 cada) | 12 | C2, C4 |
| | Alteração executada ao vivo, com o valor correto e interpretado | 6 | C4 |
| | Incerteza: leitura do intervalo de confiança e do resultado de F17 | 3 | C3 |
| | Comunicação: recomendação clara, linguagem executiva, tempo | 4 | C1 |

**Níveis:**
- Itens verificáveis (F1 a F17 e execução): certo ou errado, com a tolerância de arredondamento.
- Slide e vídeo, em cada critério:
  - **excelente:** pontuação cheia; completo, específico, apoiado nos seus números;
  - **adequado:** cerca de metade dos pontos; parcial ou genérico;
  - **insuficiente:** zero; ausente ou incorreto.

**Correção:**
- **Notebook:** automática, com base nas definições acima.
- **Slide:** aplicação da rubrica com apoio de uma ferramenta de IA (Claude), com revisão do professor.
- **Vídeo:** avaliado pelo professor, um a um.

O professor revisa uma amostra das correções automáticas e todos os casos sinalizados. Você pode pedir revisão em até 7 dias após a divulgação da nota.

## f) Exemplo resumido de um bom slide (fictício)

> **Título:** "O frete consome 16% do valor dos produtos, e os itens acima de 10 kg pagam quase 3 vezes mais"
> **Para:** Diretora Financeira · **Pergunta:** quanto o frete pesa no faturamento e onde concentrar a renegociação com transportadoras?
> **Insights:** (1) o frete soma 16,2% do valor dos produtos (F12); (2) o frete mediano é R$ 16,22, mas chega a R$ 43,97 na faixa acima de 10 kg; (3) atrasos derrubam a nota em 1,8 ponto (IC 95%: −1,88 a −1,68), e 16% dos pedidos têm experiência ruim.
> **Ações:** (1) renegociar o frete acima de 10 kg, com meta de 14% de participação do frete em 6 meses; (2) piloto de transportadora regional em dois estados, comparado com estados sem piloto; (3) painel mensal de frete por faixa de peso, revisado pela diretoria.
> **Limitação:** um terço dos pedidos atrasados não tem avaliação, contra 3% dos entregues no prazo, então a queda de nota pode estar subestimada. A distância da entrega não está na base.
> **Gráfico:** frete mediano por faixa de peso, com o título "Acima de 10 kg, o frete quase triplica".

Os números acima são de uma base de exemplo. **A sua base tem outros números.**

## g) Regras de uso de IA generativa, fontes e plágio

**Permitido:** usar assistentes de IA (ChatGPT, Claude, Gemini e outros) como **tutor**: entender uma mensagem de erro, revisar a sintaxe de um comando, explicar um conceito estatístico.

**Não permitido:**
- pedir que a IA faça a análise, monte o slide ou prepare as respostas do vídeo por você;
- usar no vídeo um roteiro escrito por outra pessoa ou por IA;
- compartilhar código, respostas ou slide com colegas.

**Declaração obrigatória:** preencha a `DECLARACAO_IA` dizendo se e como usou IA. Declarar o uso de forma honesta não tira pontos.

**Por que o desenho do trabalho importa:**
- sua base, seu cenário e suas perguntas do vídeo são **individuais**;
- as regras de negócio foram dadas **em aula**;
- no vídeo você precisa executar uma alteração **ao vivo** e explicar as **suas** decisões e os **seus** resultados.

Copiar de um colega ou de uma IA não produz os seus números nem as suas respostas.

**Fontes:** cite no slide (em nota de rodapé) qualquer fonte externa usada.

**Plágio:** slides muito parecidos entre alunos, ou incompatíveis com o domínio demonstrado no vídeo, são sinalizados para revisão do professor e tratados conforme o regulamento da FGV.

## h) Bases públicas para aprofundar (opcional, fora da nota)

Para quem quiser repetir o método em outros dados depois da disciplina:

| Base | Fonte | Bom para |
|---|---|---|
| Série histórica de preços de combustíveis | [ANP](https://www.gov.br/anp/pt-br/centrais-de-conteudo/dados-abertos/serie-historica-de-precos-de-combustiveis) | Energia; preços por região; séries temporais |
| Cartão de Pagamento do Governo Federal | [Portal da Transparência](https://portal.transparencia.gov.br/download-de-dados/cpgf) | Auditoria; outliers; setor público |
| Brazilian E-Commerce Public Dataset (base completa) | [Kaggle – Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) | Varejo; logística; textos de avaliações |
| Carga de energia e geração | [ONS – Dados Abertos](https://dados.ons.org.br) | Previsão de carga; indústria de energia |
| Dados meteorológicos históricos | [INMET](https://portal.inmet.gov.br/dadoshistoricos) | Clima; cruzamento com carga e vendas |
| Tabelas do IBGE | [SIDRA](https://sidra.ibge.gov.br) | Indicadores socioeconômicos; redução de dimensionalidade |
| Fundos e companhias abertas | [CVM – Dados Abertos](https://dados.cvm.gov.br) | Finanças; séries mensais |
| Voos e atrasos | [ANAC – dados abertos](https://www.gov.br/anac/pt-br/assuntos/dados-e-estatisticas) | Atrasos; operações; outliers |
| Portal Brasileiro de Dados Abertos | [dados.gov.br](https://dados.gov.br) | Catálogo geral do governo federal |
| Dados eleitorais | [TSE – Dados Abertos](https://dadosabertos.tse.jus.br) | Setor público; agregações por município |
