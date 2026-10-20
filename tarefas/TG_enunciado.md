# Trabalho em grupo – A frota nova da Horizonte
**Métodos e Ferramentas de Data Science – FGV MBA** · Em grupo (até 3 alunos), entrega individual · **30% da nota final**

## O que é
A história continua de onde o NB01 parou. A Marina, gerente de frota da Horizonte Distribuidora (empresa fictícia), vai abrir uma filial com carros 0 km e tem três SUVs do mesmo porte na mesa: um **a combustão**, um **híbrido** e um **elétrico**. O seu grupo responde, para o estado da filial e a quilometragem do briefing:

1. Etanol ou gasolina no carro a combustão?
2. Quanto custa a energia de um ano de cada carro?
3. Somando o IPVA do 1º ano, quanto custa o carro mais barato?
4. A diferença de preço do elétrico se paga? (payback)
5. E se a conta de luz tiver imposto?

E mais duas perguntas sobre as Aulas 2 e 3. No fim, a resposta para a Marina: um gráfico e um e-mail curto, o que você mostraria a quem decide.

**Dados (todos públicos):** preços dos combustíveis da ANP (1º semestre de 2026, a mesma base do NB01), tarifa residencial de energia da ANEEL, consumo dos carros do Inmetro (PBE Veicular 2026) com valor FIPE, e alíquotas de IPVA 2026 por estado. Detalhes em `dados/README.md`.

**Conteúdo:** o que vimos até a Aula 3 (NB01a e NB01): filtrar, `groupby`, `mean`, coluna nova e gráfico. O que for novo (buscar um valor com `.loc`, `min`, `idxmin`) está explicado no notebook, antes de cada célula. As lacunas `____` marcam o que completar.

**Tempo estimado:** de 4 a 6 horas para o grupo. Vocês começam no fim da Aula 3.

## Grupos
- De 1 a 3 alunos. Combinem o grupo até o fim da Aula 3.
- Cada grupo recebe um **briefing**: o estado da filial e quantos km cada carro roda por ano. Ele é sorteado no notebook pela **menor matrícula** do grupo. Por isso, **todos do grupo digitam exatamente a mesma lista de matrículas**.
- A matrícula, nesta disciplina, é o seu nome de usuário do ECLASS (por exemplo, `A12345678`).

## Como entregar (cada aluno entrega)
1. Abra o notebook `tarefas/TG_trabalho_grupo.ipynb` no Colab: [abrir no Colab](https://colab.research.google.com/github/carloscarlim/fgv-mfds/blob/main/tarefas/TG_trabalho_grupo.ipynb). Clique em *Arquivo → Salvar uma cópia no Drive*.
2. Preencha a sua matrícula e a lista do grupo; execute o sorteio do briefing.
3. Faça as partes 1 a 8 e execute o **verificador de formato** no fim. Corrija o que ele apontar.
4. Baixe o notebook **já executado** (*Arquivo → Fazer download → Baixar o .ipynb*), renomeie para `TG_<sua matrícula>.ipynb`, com **a sua própria matrícula**, não a que sorteou o briefing (exemplo: `TG_A12345678.ipynb`), e envie na atividade do ECLASS. Cada aluno do grupo entrega o seu arquivo.

**Prazo:** 23h59 da véspera da Aula 4 (data exata no ECLASS).

## Nota
- **P1 a P10:** 0,8 ponto cada (8 pontos). Os números valem como o verificador mostra: valores em reais sem centavos e o payback com uma casa decimal.
- **E-mail para a Marina:** 2 pontos, 0,5 por item: a recomendação, com o número que a sustenta; o que muda se a conta de luz tiver tributos; o cuidado antes de assinar o pedido; clareza (até 4 frases, para quem decide, sem código e sem jargão).
- Todos do grupo entregam o mesmo trabalho, cada um com a sua matrícula. Se as entregas de um mesmo grupo forem diferentes, o professor confere.
- Pedidos de revisão: até 7 dias depois da divulgação da nota.

## Regras
- **Grupo:** o código e as respostas são do grupo. Não compartilhe com outros grupos.
- **Uso de IA generativa:** pode usar como tutor (entender um erro, revisar um comando, explicar um conceito). Não pode pedir que ela faça a análise por você.
- **Atrasos:** seguem o regulamento acadêmico da FGV.

**Dúvidas:** fórum do ECLASS.
