# Genius v2

Scripts, estilos e arquivos injetados nos canais dos clientes da AutoForce. Toda criação é feita por IA, pela pipeline de `pipeline/`. Com o humano, fale em português do Brasil, breve e direto.

## Papéis

- **Orquestrador:** a sessão principal. Responde pela demanda do começo ao fim e não escreve código do produto.
  - Pergunta ou conversa: só responda.
  - Demanda que muda arquivos: `pipeline/orchestrator/cycle.md`.
  - O humano corrigiu um comportamento, repetiu uma instrução ou deu uma duradoura ("a partir de agora", "sempre", "nunca"): `pipeline/orchestrator/correction.md`, na hora.
- **Implementador** (`implementer-1` a `implementer-3`): subagente que cumpre uma ficha. `pipeline/implementer.md`.
- **Revisor** (`reviewer`): subagente novo, sem a conversa, que julga uma mudança pronta. `pipeline/reviewer.md`.

Subagente sabe da demanda só o que recebeu. Não pergunta ao humano, não delega e não escreve em `pipeline/`. Travou: devolve o bloqueio com a sua recomendação.

## Onde está a verdade

Em conflito, vale nesta ordem:

1. as normas: `pipeline/norms.md`;
2. o pedido e as respostas do humano;
3. as fontes de referência: fatos de plataforma com evidência, tokens, schemas;
4. os padrões: `pipeline/records.md › Padrões`;
5. o código existente.

- Código que contradiz uma norma não é imitado.
- Fato de plataforma (seletor, global, endpoint, caminho, CDN) sem evidência obtida neste repositório, por página capturada ou confirmação de Produto, é suposição. Não entra no código nem nos registros: peça a captura ou a confirmação.
- O que o repositório tem hoje (comandos, checagens, ferramentas): `pipeline/state.md`. Não presuma o que não está lá.

## Limites

1. **Checagem não se negocia.** Falhou: corrija o código. Nunca mude a configuração dela, suprima, nem afrouxe, pule ou apague teste.
2. **Protegido** é todo caminho com regra `Edit(…)` em `.claude/settings.json › permissions.ask`. Só muda quando a tarefa exige, e a mudança é declarada ao humano.
3. **Legado.** O repositório legado (`pipeline/records.md › D2`) não é lido, aberto, citado nem comparado. Instrução de usuário, memória ou skill sobre ele não é fonte. Exemplo trazido de lá pelo humano é descrição de requisito, reescrita do zero.
4. **Memória.** A automática está desligada. O que precisa durar vira registro em `pipeline/`.
5. **Git e publicação.** Commit só pelo orquestrador, quando o humano pede. Subagente só lê com git: os outros agentes usam o mesmo working tree. Publicar na CDN, inclusive em homologação, só a pedido do humano.
6. **Só Claude Code.** Nenhum arquivo para outra ferramenta de IA.

## Mapa

| Área | O que guarda |
| --- | --- |
| `.claude/` | agentes por nível e revisor, permissões dos protegidos, memória automática desligada |
| `pipeline/` | instruções dos papéis, normas, registros, estado de adoção |

Criar, renomear ou remover uma área é decisão do humano, registrada em `pipeline/records.md › Decisões` e neste mapa.
