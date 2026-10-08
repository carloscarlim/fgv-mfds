# Tarefa 2 – Python básico e da pergunta à técnica
**Métodos e Ferramentas de Data Science – FGV MBA** · Individual · Vale 7,5% da nota final

**Objetivo:** (A) praticar os fundamentos de Python vistos no NB02, escrevendo funções que resolvem pequenos problemas de negócio; (B) classificar perguntas de negócio pela técnica de Ciência de Dados adequada; (C) formular uma pergunta de negócio da sua área.
A tarefa prepara a Aula 3, em que vamos usar o pandas para analisar a base de e-commerce Olist.

**Prazo:** 23h59 da véspera da Aula 3. **Tempo estimado:** até 1h30.

**Como entregar**
1. Abra no Colab e clique em *Arquivo → Salvar uma cópia no Drive*.
2. Preencha sua matrícula e execute a célula do sorteio.
3. Resolva as partes A, B e C. Use a célula de autoteste da Parte A para conferir suas funções.
4. Execute o **verificador de formato** no fim. Baixe o arquivo (*Arquivo → Fazer download → .ipynb*), renomeie para `T2_<sua matrícula>.ipynb` e envie no ECLASS.

**Regras**
- Correção **automática**. Na Parte A, suas funções são testadas com casos que você não vê (além dos do autoteste). Não mude o nome das funções nem dos parâmetros.
- As perguntas da Parte B são sorteadas pela sua matrícula.
- Você pode usar assistentes de IA para tirar dúvidas, mas o texto da Parte C deve ser seu. Textos iguais entre alunos vão para revisão do professor. Textos com mais de 100 palavras são cortados na 100ª palavra.

**Leitura preparatória para a Aula 3:** CARVALHO, MENEZES & BONIDIA, *Ciência de dados: fundamentos e aplicações* (LTC, 2024), tema: preparação e manipulação de dados [VERIFICAR CAPÍTULO].

**Rubrica (10 pontos)**

| Critério | Pontos | Insuficiente | Adequado | Excelente |
|---|---|---|---|---|
| Parte A: funções (F1 a F5) | 5,0 | Funções não rodam ou falham na maioria dos testes | Passam em parte dos testes | Passam em todos os testes |
| Parte B: técnica das 6 perguntas | 1,8 | Menos da metade correta | Metade ou mais correta | Todas corretas |
| Parte B: supervisionado e estruturado | 1,8 | Menos da metade correta | Metade ou mais correta | Todas corretas |
| Parte C: sua pergunta de negócio | 1,4 | Pergunta ausente ou genérica | Faltam elementos ou a técnica não combina com a pergunta | Pergunta, técnica, dado e medida de sucesso coerentes |

## Parte B – Da pergunta à técnica
Para cada uma das **suas 6 perguntas** (mostradas na célula do sorteio), responda na célula RESPOSTAS:
- **técnica:** `"classificacao"`, `"previsao"`, `"agrupamento"`, `"reducao"` (redução de dimensionalidade) ou `"anomalia"` (detecção de anomalias);
- **supervisionado:** `True` ou `False`;
- **estruturado:** `True` se o dado principal é tabela/número, `False` se é texto, imagem ou áudio.

Use o glossário do simulador da Aula 2 (aba *Jogo do mapeamento*).

## Parte C – Sua pergunta de negócio
Em até 100 palavras, escreva uma pergunta de negócio **da sua área de trabalho** que poderia ser respondida com Ciência de Dados. Inclua:
1. a pergunta;
2. a técnica (e se é supervisionada e se o dado é estruturado);
3. que dado seria necessário e onde ele está na empresa;
4. como você saberia se funcionou (uma medida de sucesso).
