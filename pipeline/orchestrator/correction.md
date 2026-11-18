# Correção da pipeline

A pipeline muda quando causa ou não evita um problema. Tarefa sem gatilho não escreve em `pipeline/`.

## Gatilhos

- Do humano: os de `CLAUDE.md › Papéis`. Instrução sem sinal de que dura vale só para a tarefa.
- Seus: falha de causa pipeline; item de `Registro` ou `Pipeline:` confirmado no código; problema que uma linha já cobria e voltou; instrução que causou retrabalho ou pergunta desnecessária; referência quebrada ou instrução contraditória vista de passagem.

Não é gatilho: erro isolado que a conferência pegou; primeira ocorrência de uma forma; tarefa que correu bem.

## Instrução duradoura

Vira registro na hora, na mesma tarefa, pelo `Onde mora`. A instrução do humano já é a aprovação. Norma nova traz motivo e checagem, `prevista` enquanto a ferramenta não existe. Declare na entrega.

## Passos

1. **Efeito:** corrija o problema da tarefa pelo caminho normal.
2. **Causa:** ache a linha que deixou acontecer: ausente, ambígua, contraditória, velha, não lida (nenhum gatilho levou a ela) ou ignorada (lida e não seguida).
3. **Remédio:** o primeiro que remove a causa.
   1. Nada: um agente competente, com o código e as normas de hoje, acertaria, ou a conferência pega.
   2. Apagar ou reescrever: ambígua, contraditória ou velha. Sem linha nova.
   3. Checagem ou código: uma ferramenta pode recusar o erro sem exceção caso a caso. Faça uma ficha; a norma ganha a checagem.
   4. Posição: não lida, ou ignorada que nada pega. Leve a linha para o momento da ação (modelo da ficha, `pipeline/implementer.md › Antes de retornar`, `pipeline/orchestrator/cycle.md › 5. Confira`). Nunca uma segunda linha.
   5. Texto novo: só para ausente, e só se passa em `Entra em pipeline/`.
   6. Humano: a linha já está no momento da ação e o problema voltou. Leve o diagnóstico e as opções.
4. **Prova:** releia como um agente novo, que carrega só o que os gatilhos mandam. Ele acertaria agora?
5. **Aprovação:** fora a instrução duradoura do humano, proponha na entrega o texto, o motivo com a evidência e as alternativas. Aplique com o ok dele.
6. **Ocorrência:** registre em `pipeline/records.md › Ocorrências`.

## Entra em `pipeline/`

Uma linha nova responde sim às três:

1. Um agente que lê o código, a árvore, a configuração e a documentação oficial erraria sem ela?
2. Nenhuma checagem recusa o erro, nem pode recusar a custo razoável?
3. Nenhuma linha cobre o assunto? Se cobre, edite-a.

Nunca entra: o que o código mostra (caminho, nome, assinatura, lista do que existe), histórico, intenção ainda não implementada.

## Onde mora

| O que é | Onde |
| --- | --- |
| Obrigação ou proibição verificável no código | `pipeline/norms.md` |
| Forma de fazer um tipo de coisa, com exemplar | `pipeline/records.md › Padrões` |
| Armadilha que o código não mostra | `pipeline/records.md › Particularidades` |
| Decisão do humano | `pipeline/records.md › Decisões` |
| Correção da pipeline | `pipeline/records.md › Ocorrências` |
| Comando, checagem, ferramenta, protegido, recurso exclusivo | `pipeline/state.md` |
| Fato de plataforma | `pipeline/state.md › Fatos de plataforma` |
| Processo de um papel | o arquivo do papel |
| O que vale para todo agente | `CLAUDE.md` |

## Como escrever

- Cada linha muda a decisão de um agente. Se um agente competente faria o mesmo sem ela, ela sai.
- Frases curtas, listas, sem preâmbulo e sem exemplo que não mude a decisão. Uma obrigação por item.
- Obrigação no imperativo; proibição com `Nunca` ou `Não`; exceção com `Exceto`; motivo com `Porque`, só quando não é óbvio.
- Cada regra numa fonte só. Nos outros lugares, aponte: `arquivo › título`.
- Só o estado atual. O histórico fica no git.
- Caminhos, comandos e identificadores entre crases, conferidos.
- Mudou título, caminho, ID ou nome de agente: busque as citações no repositório e atualize todas.

## Orçamento

Em bytes UTF-8. Passou do teto: corte antes de acrescentar.

| O quê | Teto |
| --- | --- |
| `CLAUDE.md` | 4 KB |
| Cada arquivo de `pipeline/` | 8 KB |
| Cada definição em `.claude/agents/` | 1 KB |
| Orquestrador, caminho curto: `CLAUDE.md`, `cycle.md`, `state.md`, `norms.md`, `records.md` | 22 KB |
| Orquestrador, tudo: o caminho curto mais `waves.md`, `review.md` e `correction.md` | 32 KB |
| Implementador: a definição, `CLAUDE.md`, `implementer.md`, `norms.md` | 12 KB |
| Revisor: a definição, `CLAUDE.md`, `reviewer.md`, `norms.md`, `records.md`, `state.md` | 16 KB |

Checagem: prevista.
