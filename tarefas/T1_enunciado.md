# Tarefa 1 – Diagnóstico: do dado à decisão
**Métodos e Ferramentas de Data Science – FGV MBA** · Individual · Vale 7,5% da nota final

**Objetivo:** praticar dois movimentos da Aula 1: (A) ler dados com Python para responder a uma pergunta de negócio e (B) avaliar o valor, as restrições e os riscos de uma aplicação de Ciência de Dados.
A tarefa prepara a Aula 2, em que vamos ligar perguntas de negócio às técnicas de CD.

**Prazo:** 23h59 da véspera da Aula 2. **Tempo estimado:** até 1h30.

**Como entregar**
1. Abra este notebook no Colab e clique em *Arquivo → Salvar uma cópia no Drive*.
2. Preencha sua matrícula na primeira célula de código e resolva as partes A e B.
3. Copie suas respostas para a célula **RESPOSTAS**, no fim, e execute o **verificador de formato**.
4. Baixe o arquivo (*Arquivo → Fazer download → .ipynb*), renomeie para `T1_<sua matrícula>.ipynb` e envie no ECLASS.

**Regras**
- A correção é **automática**: números são conferidos com o gabarito da **sua** matrícula, e os textos são avaliados com a rubrica abaixo. Respostas fora do formato da célula RESPOSTAS não são lidas.
- Seus dados e parâmetros são **individuais**, definidos pela sua matrícula. Copiar respostas de colegas não funciona.
- Você pode usar assistentes de IA para tirar dúvidas, mas os textos devem ser seus. Textos iguais entre alunos são enviados para revisão do professor.
- Textos com mais de 80 palavras são cortados na 80ª palavra antes da avaliação.

**Leitura preparatória para a Aula 2:** CARVALHO, MENEZES & BONIDIA, *Ciência de dados: fundamentos e aplicações* (LTC, 2024), tema: tarefas preditivas e descritivas (classificação, regressão e agrupamento).

**Rubrica (10 pontos)**

| Critério | Pontos | Insuficiente | Adequado | Excelente |
|---|---|---|---|---|
| Parte A: dados do seu estado (A1 a A6) | 5,0 | Valores ausentes ou de outro estado | A maioria dos valores corretos | Todos os valores corretos |
| Parte B: objetivo e tipo de uso (B1, B2) | 1,5 | Classificação incorreta | Uma das duas correta, ou B1 parcialmente correta | Ambas corretas |
| Parte B: valor e acerto mínimo (B3, B4) | 2,0 | Valores incorretos | Um dos dois correto | Ambos corretos |
| Parte B: risco e mitigação (B5) | 0,75 | Não identifica risco relevante | Identifica risco **ou** mitigação, de forma genérica | Risco concreto do caso **e** mitigação coerente |
| Parte B: recomendação (B6) | 0,75 | Ausente ou contraditória | Recomendação sem condição ou sem ligação com os números | Recomendação clara, apoiada nos números, com condição verificável |

## Parte B – Caso: Litoral Energia *(empresa fictícia)*

A Litoral Energia é uma distribuidora de eletricidade que perde parte da energia que compra por **furtos e fraudes em medidores** (as chamadas *perdas não técnicas*, ou "gatos").
Para combater o problema, a empresa mantém equipes que visitam imóveis para inspecionar os medidores. Hoje, **a maioria das inspeções não encontra irregularidade**: a equipe vai, confere e volta sem resultado.

O conselho de administração já aprovou o programa de combate a perdas. Agora, a diretoria de operações quer usar um modelo de Ciência de Dados que, **toda semana, indica quais imóveis as equipes devem inspecionar**.
O modelo usaria histórico de consumo de cada cliente, atrasos de pagamento, localização e denúncias anteriores.
O diretor resume: *"Quero menos viagens perdidas e mais energia recuperada."*

Dois pontos preocupam o comitê:
- Uma auditoria interna mostrou que as inspeções antigas se concentraram em bairros de baixa renda. O histórico, portanto, tem **mais irregularidades registradas onde mais se inspecionou**.
- Dados de consumo e de pagamento de cada cliente são **dados pessoais**.

Os números do caso (abaixo) são **seus**, sorteados pela sua matrícula. Use o mesmo modelo da Calculadora de Valor e Risco da aula, com adoção de 100%:

> **Valor líquido anual** = volume × (acerto × ganho − (1 − acerto) × perda − custo por decisão) − custo fixo − risco esperado

O **acerto mínimo para empatar** é a taxa de acerto em que o valor líquido anual é zero.
