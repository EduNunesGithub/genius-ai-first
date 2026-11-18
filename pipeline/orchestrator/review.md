# Revisão

A mudança tem sinal de risco (`pipeline/orchestrator/cycle.md › 7. Verifique`).

## Quando

- Uma revisão do conjunto, depois de integrar tudo e passar as checagens completas. Nunca uma por ficha.
- Antecipada: o exemplar arriscado que outras fichas vão replicar. Não conta nos ciclos.

## Pedido

- Sempre um `reviewer` novo: nunca fork desta conversa nem continuação de outro revisor.
- O pedido traz só este modelo. Nunca fichas, raciocínio ou resumo da implementação.
  - Porque: o valor do revisor está em julgar sem herdar as suposições de quem fez.

```markdown
Objetivo: <o que o humano pediu, como resultado>
Critérios: <o que precisa valer: do pedido, das respostas e do que o objetivo implica>
Escolhas: <as suas onde o pedido não dizia nada, inclusive protegido alterado, com o motivo>
Base: <referência à base, ou o diff só da mudança, com arquivos novos e apagados>
Achados anteriores: <só no segundo ciclo>
```

## Ciclos

No máximo dois:

1. Revisão do conjunto.
2. Só se houve correção de `quebra`, ou correção que mudou lógica ou contrato: revisor novo, com `Achados anteriores` e a `Base` no estado revisado.

- Antes de mandar corrigir, guarde o estado revisado.
- Sobrou do segundo: `quebra`, corrija pela causa e confirme você mesmo, reproduzindo a evidência; `destoa`, proposta na entrega.
- `Incompleta:` não conta como ciclo. Chame um revisor novo uma vez; repetiu, diga na entrega.

## Achados

1. **Confirme** reproduzindo ou seguindo o código. Sem base: descarte.
2. **Escopo:** no que a demanda mudou, corrija agora (`pipeline/orchestrator/cycle.md › 6. Falha`). No que ela não tocou, `quebra` vira pergunta na entrega e o resto se descarta.
3. **`Pipeline:`** é indício, não prova. Confirmado no trecho: `pipeline/orchestrator/correction.md`.
