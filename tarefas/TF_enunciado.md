# Trabalho Final – Análise exploratória para a diretoria
**Métodos e Ferramentas de Data Science – FGV MBA** · Individual · **70% da nota final**

## a) O desafio

Você é o analista de dados de um e-commerce. A sua diretoria tem uma dor de negócio e pediu uma análise que a ajude a decidir.

Cada aluno recebe:
- **uma base individual**: 20% dos pedidos da Olist (e-commerce brasileiro, 2016–2018), sorteados pela sua matrícula, em três tabelas (`pedidos`, `itens`, `avaliacoes`). Como toda base real, ela tem **problemas de qualidade** que você precisa encontrar e tratar;
- **um cartão de cenário**: quem é a sua diretoria, qual a dor dela e uma métrica obrigatória.

O notebook-modelo `tarefas/TF_trabalho_final.ipynb` carrega a sua base e mostra o seu cartão. Você vai:
1. formular uma **pergunta de negócio** a partir do cartão;
2. **descrever e tratar** a base, documentando cada decisão;
3. fazer a **análise exploratória**: distribuições, outliers, correlação, comparação de grupos e intervalo de confiança;
4. responder às **perguntas verificáveis** (F1 a F12);
5. escrever um **memorando executivo** de até 400 palavras;
6. gravar um **vídeo de até 8 minutos** respondendo a perguntas feitas só para você, a partir do seu notebook.

As **regras de negócio** apresentadas nas aulas valem para o trabalho. Se faltar a uma aula, assista à gravação.

## b) Marcos e prazos

Os marcos são **obrigatórios e não valem nota**. Eles geram uma devolutiva automática para você melhorar antes da entrega final e fazem parte do registro do seu processo. Entregas finais sem marcos são revisadas pelo professor.

| Marco | O que entregar (no mesmo notebook, com `ETAPA` ajustada) | Prazo |
|---|---|---|
| Marco 1 | Pergunta de negócio, técnica, dados necessários e medida de sucesso (`MARCO1`) | 23h59 da véspera da Aula 3 |
| Marco 2 | Base inspecionada e dicionário de dados com as 12 colunas (`DICIONARIO`) | 23h59 da véspera da Aula 4 |
| Marco 3 | Limpeza documentada e as respostas F1 a F11 que já conseguir calcular | 23h59 da véspera da Aula 5 |
| **Entrega final** | Notebook completo, respostas F1 a F12, memorando e declaração de uso de IA | **23h59 do 7º dia depois da Aula 5** |
| Perguntas do vídeo | Você recebe por e-mail as suas perguntas personalizadas | Até 24 h depois do prazo da entrega final |
| **Vídeo** | Até 8 minutos | **72 h depois de receber as perguntas** |

**Como enviar:** o notebook (`.ipynb`) no ECLASS, com o nome `TF_<sua matrícula>.ipynb`; o vídeo (`.mp4`) no ECLASS com o nome `<sua matrícula>.mp4`. Se o arquivo passar do limite de tamanho do ECLASS, envie um link do Google Drive compartilhado só com ext.carlos.pinto@prof.fgv.br.

## c) Estrutura do entregável

**1. Notebook** (o modelo já traz as seções):
- seções 0 e 1: matrícula, etapa, base e cartão;
- seção 2: Marco 1;
- seção 3: inspeção e dicionário de dados;
- seção 4: limpeza e análise, com **células de texto explicando cada decisão e cada achado**;
- seção 5: respostas verificáveis F1 a F12;
- seção 6: memorando;
- seção 7: declaração de uso de IA;
- seção 8: verificador (execute antes de cada envio).

O notebook precisa **rodar do início ao fim sem erro** (*Ambiente de execução → Reiniciar e executar tudo*).

**2. Definições das respostas verificáveis** (siga exatamente: a correção é automática)

| Item | Definição |
|---|---|
| F1 | Linhas de `pedidos` idênticas em todas as colunas, removidas (mantém uma de cada) |
| F2 | Entre os pedidos com `order_status == "delivered"` e data de entrega não nula: prazo `(entrega − compra).dt.days` negativo ou acima de 365 dias. Esses pedidos ficam fora das análises de prazo e atraso. Os demais são os **pedidos entregues válidos** |
| F3 | Número de fretes corrigidos pela regra de negócio da Aula 4 |
| F4 | Número de itens com frete igual a zero na base tratada (aplique a regra de negócio da Aula 3) |
| F5 | Linhas de `itens` cuja categoria muda ao padronizar com `.str.strip().str.lower()` |
| F6 e F7 | Prazo mediano (dias) e porcentagem de atraso (`entrega > data estimada`) dos pedidos entregues válidos |
| F8 | Mediana e média de `freight_value` em todos os itens da base tratada |
| F9 | Correlação de Spearman entre `freight_value` e `product_weight_g`, nos itens com peso maior que zero |
| F10 | Nota de cada pedido = média de `review_score` por `order_id`. Diferença: nota média dos atrasados − nota média dos no prazo (pedidos entregues válidos com nota). Intervalo de confiança de 95%: diferença ± 1,96 × √(s²₁/n₁ + s²₂/n₂) |
| F11 | Porcentagem dos pedidos entregues válidos **sem nota**, entre os atrasados e entre os no prazo |
| F12 | A métrica do seu cartão de cenário |

Porcentagens de 0 a 100 com 2 casas; dias, reais e notas com 2 casas; correlação com 3 casas.

**3. Memorando executivo** (até 400 palavras, dentro do notebook), para a diretoria do seu cartão:
1. Pergunta de negócio.
2. Achados, com números da sua base (inclua F12).
3. Incerteza e limitações.
4. Recomendação, com uma condição verificável.
5. Decisões de limpeza que afetam os números.

## d) O vídeo (no lugar da apresentação oral)

- Até **8 minutos**. Acima de 8 minutos, há desconto de 2 pontos.
- **Câmera ligada** num canto da tela e o **seu notebook aberto** na tela durante todo o vídeo.
- Responda, na ordem, às perguntas que você receber:
  - três perguntas sobre as **suas** decisões e números;
  - **uma alteração para executar ao vivo** no notebook (por exemplo, recalcular algo com outro parâmetro e dizer o resultado);
  - uma pergunta de **inferência**;
  - **um minuto de recomendação** para a diretoria.
- Não é preciso editar nem ter produção caprichada: vale o raciocínio. Você pode gravar com o próprio Google Meet, Zoom, Teams ou o gravador de tela do computador.
- **Privacidade:** o vídeo é usado só para a avaliação, fica numa pasta restrita e é apagado ao fim do prazo de revisão de notas.

## e) Rubrica (70 pontos)

| Componente | Critério | Pontos | Competências |
|---|---|---|---|
| **Notebook (25)** | Preparação dos dados: F1 a F5 corretos | 10 | C2, C4 |
| | Rigor da EDA: F6 a F12 corretos | 10 | C2, C3 |
| | Qualidade do código: roda do início ao fim sem erro | 3 | C4 |
| | Decisões de limpeza e achados documentados em texto | 2 | C2 |
| **Memorando (20)** | Qualidade da pergunta de negócio, ligada ao cartão | 4 | C1 |
| | Interpretação e insights: achados com números corretos da sua base | 6 | C2, C3 |
| | Limitações e incerteza | 5 | C2 |
| | Recomendação acionável, com condição verificável | 5 | C1 |
| **Vídeo (25)** | Respostas às três perguntas personalizadas (4 cada) | 12 | C2, C4 |
| | Alteração executada ao vivo com o valor correto | 6 | C4 |
| | Inferência: leitura do intervalo e efeito dos faltantes | 3 | C3 |
| | Comunicação: recomendação clara, linguagem executiva, tempo | 4 | C1 |

**Níveis:**
- Itens verificáveis (F1 a F12 e execução): certo ou errado, com a tolerância de arredondamento.
- Memorando e vídeo, em cada critério:
  - **excelente:** pontuação cheia; completo, específico, apoiado nos seus números;
  - **adequado:** cerca de metade dos pontos; parcial ou genérico;
  - **insuficiente:** zero; ausente ou incorreto.

**Correção:** automática, com apoio do Claude (Anthropic) para memorando e vídeo, a partir desta rubrica. O professor revisa uma amostra e todos os casos sinalizados. Você pode pedir revisão em até 7 dias após a divulgação da nota.

## f) Exemplo resumido de um bom trabalho (fictício)

> **Cartão:** Diretora Financeira – "Quanto o frete pesa no faturamento?"
> **Pergunta:** "Quanto o frete pesa no faturamento e em que tipo de produto concentrar a renegociação com transportadoras?"
> **Limpeza documentada:** removi 156 pedidos duplicados; excluí 31 entregas com datas impossíveis das análises de prazo; corrigi 41 fretes e mantive 313 itens de frete zero, conforme as regras de negócio; padronizei 763 categorias.
> **Achados:** o frete soma 16,2% do valor dos produtos; o frete mediano é R$ 16,19 e a média R$ 19,82, puxada por itens pesados (Spearman frete × peso = 0,45); atrasados têm nota 1,78 ponto menor (IC 95%: −1,88 a −1,68).
> **Limitações:** 33% dos atrasados não avaliaram, contra 3% dos no prazo, então a diferença de nota pode estar subestimada; não temos a distância de entrega; dados de 2016–2018.
> **Recomendação:** renegociar primeiro o frete de produtos acima de 10 kg, com meta de reduzir a participação do frete para 14% em 6 meses, comparando com categorias não renegociadas.

Os números acima são de uma base de exemplo. **A sua base tem outros números.**

## g) Regras de uso de IA generativa, fontes e plágio

**Permitido:** usar assistentes de IA (ChatGPT, Claude, Gemini e outros) como **tutor**: entender uma mensagem de erro, revisar a sintaxe de um comando, explicar um conceito estatístico.

**Não permitido:**
- pedir que a IA faça a análise, escreva o memorando ou prepare as respostas do vídeo por você;
- usar no vídeo um roteiro escrito por outra pessoa ou por IA;
- compartilhar código, respostas ou memorando com colegas.

**Declaração obrigatória:** preencha a `DECLARACAO_IA` dizendo se e como usou IA. Declarar o uso de forma honesta não tira pontos.

**Por que o desenho do trabalho importa:**
- sua base, seu cenário e suas perguntas do vídeo são **individuais**;
- as regras de negócio foram dadas **em aula**;
- no vídeo você precisa executar uma alteração **ao vivo** e explicar as **suas** decisões.

Copiar de um colega ou de uma IA não produz os seus números nem as suas respostas.

**Fontes:** cite no memorando qualquer fonte externa usada (dados, artigos, referências da bibliografia).

**Plágio:** textos muito parecidos entre alunos, ou incompatíveis com o domínio demonstrado no vídeo, são sinalizados para revisão do professor e tratados conforme o regulamento da FGV.

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
