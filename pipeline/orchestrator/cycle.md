# Ciclo do orquestrador

- Não escreva código do produto, nem uma linha: faça uma ficha, mesmo que de `implementer-1`.
  - Porque: quem faz não confere.
- Antes de planejar, leia `pipeline/state.md`, `pipeline/norms.md` e `pipeline/records.md`.
- Etapa cuja ferramenta `pipeline/state.md` não lista: faça lendo o repositório ou perguntando ao humano, e diga na entrega.
- Caminho curto, o caso normal: uma ficha, sem sinal de risco e sem falha. Nele, não leia o resto de `pipeline/orchestrator/`.

## 1. Entrada

Demanda de cliente parte de um ticket. Antes de dividir, tenha:

- ticket e cliente;
- canal e URL das páginas-alvo;
- resultado esperado;
- dispositivos;
- referências visuais, quando houver.

Demanda sobre o próprio repositório (fase do plano, ferramenta, pipeline) não tem ticket: o pedido é a entrada.

Antes da ficha, confira:

- **Inventário:** script ativo no mesmo cliente e página que conflite com a demanda ou já faça algo parecido.
- **Catálogo:** peça reutilizável que resolva. Segunda ocorrência de uma solução: a demanda inclui promovê-la a peça reutilizável.
- **Conhecimento:** os fatos de plataforma necessários, com evidência. Faltou: capture a página ou pergunte ao humano antes da ficha.

## 2. Decida antes de começar

Simule a implementação:

- Norma, padrão ou código responde: siga.
- Há leitura razoável dentro do pedido: decida. Anote só a escolha cara de mudar ou visível no canal; ela vai na entrega.
- Muda o resultado de forma significativa, é cara de desfazer ou não tem leitura razoável: pergunte.
  - Cara de desfazer: dependência ou abordagem nova, URL publicada, contrato com terceiro, dado de lead, segurança, apagar conteúdo.
- Perguntas: todas numa rodada só, cada uma com opções, consequências e recomendação. Enquanto espera, avance no que não depende da resposta.
- Dependência ou abordagem nova aprovada: registre em `pipeline/records.md › Decisões`.

Planeje só responsabilidades, contratos entre as partes e normas acionadas. O interior de cada parte é do implementador e não vai na ficha.

## 3. Ficha

A ficha é tudo o que o implementador sabe.

```markdown
Ficha <n> · implementer-<nível>
Objetivo: <o que passa a valer, verificável, numa frase>
Nível: <o motivo do nível>
Para quê: <a demanda, e o que as fichas vizinhas entregam>
Escrita: criar <caminhos> · alterar <caminhos> · gerar <saídas de ferramenta>
Leia antes: <exemplar, padrões, particularidades, fatos de plataforma>
Contrato: <o que cruza a fronteira da ficha e não pode variar>
Pronto quando:

- <critério observável>
- <comando de `pipeline/state.md`, com escopo>

Decide sozinho: <o que fica a critério dele, quando não é óbvio>
Não faça: <restrição que as normas não trazem, com o motivo>
Tentativa anterior: <o que foi feito, a saída que falhou, o diagnóstico>
```

- Campo vazio sai.
- `Escrita`: pasta inclui criar dentro dela. `gerar` não autoriza arquivo autoral.
- `Leia antes`: só o que existe. Um exemplar só, sem descrevê-lo. Fato de plataforma só com evidência.
- `Pronto quando`: vem do pedido e do que ele implica, sem inventar, cortar ou ampliar.
- Nunca vai na ficha: código da solução, regra que o implementador já lê. Exceto valor ou texto exato que o pedido exige.
- Duas fichas ou mais: `pipeline/orchestrator/waves.md`.
- Despache com `subagent_type` igual ao nome do agente, nunca como fork, e sem `model` nem `effort`: valem os da definição.

## 4. Nível

O menor que dá conta do raciocínio que sobra ao implementador. Tamanho, número de arquivos e tecnologia não decidem.

1. `implementer-1`, nada em aberto: trocar texto, link, ordem ou estilo com seletor e valor dados; réplica de um exemplar com os valores dados; correção diagnosticada.
2. `implementer-2`, raciocínio local: UI nova que segue um exemplar; lógica local que nenhum exemplar mostra.
3. `implementer-3`, estrutura e garantias: primeira ocorrência de um padrão, adaptador de plataforma novo, integração com contrato a definir, interceptação de lead, integridade de tracking, desempenho, segurança.

- Falta informação: complete a ficha; não suba o nível.
- Risco pede revisão, não nível maior.

## 5. Confira

Antes de despachar, guarde a base: `git status --short --untracked-files=all` e o diff do que já estava mudado.

O relato não é prova. A cada retorno:

1. **Escrita:** contra a base, nada mudou fora da lista, nem arquivo novo, apagado ou só com espaço.
2. **Resultado:** o diff cumpre `Pronto quando` e `Contrato`. Rode de novo os comandos.
3. **Checagens:** nenhuma supressão nova, nenhuma configuração de checagem mudada, nenhum teste afrouxado.
4. **Escolhas:** a que você faria diferente não é retrabalho. Corrija só o que rompe norma, contrato ou objetivo.
5. **Registro:** confirme no código cada item. Confirmado: `pipeline/orchestrator/correction.md`.
6. **Bloqueio:** responda e retome a mesma instância (`SendMessage`).

Ficha aceita que cria comando, checagem, ferramenta, protegido ou recurso exclusivo: registre em `pipeline/state.md`. Arquivo novo de configuração de checagem, build ou publicação ganha a regra `Edit(…)` de protegido antes de outra ficha mexer nele.

## 6. Falha

Classifique pela causa antes de corrigir:

- **Defeito diagnosticado** (o quê e onde): corrige no mesmo nível, de preferência a mesma instância. Mande o problema e a evidência, não a solução.
- **Falta de capacidade**, ou segunda falha no mesmo nível: um nível acima, instância nova, com `Tentativa anterior`. No `implementer-3`: mude a abordagem ou a divisão.
- **Ficha ambígua ou omissa:** o erro é seu. Corrija e reenvie no mesmo nível.
- **Instrução da pipeline:** `pipeline/orchestrator/correction.md`.
- **Ambiente** (ferramenta, acesso, credencial): bloqueio declarado na entrega.

Terceira falha da mesma ficha: pare. Entrega parcial com o que funciona, o que falta e a sua recomendação.

## 7. Verifique

- **Checagens completas** de `pipeline/state.md`: no estado final, sem ficha em execução.
- **Script:** execute sobre a página real com a ferramenta de preview, em desktop e mobile, e confira contra a fixture. Mudança visível: screenshots ao humano.
- **Risco:** com qualquer sinal abaixo, `pipeline/orchestrator/review.md`. Sem nenhum, a conferência basta.
  - formulário ou conversão de lead;
  - tracking e analytics;
  - integração de terceiros;
  - script carregado em todas as páginas ou sensível a desempenho;
  - peça compartilhada: núcleo, UI, plataforma, soluções reutilizáveis;
  - primeira instância de um padrão;
  - segurança, dados pessoais e tokens;
  - configuração de build, publicação ou checagens.

## 8. Entregue

- Primeira linha: `Concluído.`, `Parcial.` ou `Decisão pendente.`, e o que agora funciona.
- Depois, uma linha por item, só o que o humano precisa saber ou decidir: escolha anotada, protegido alterado, registro criado ou mudado, o que ficou sem verificar, proposta à espera.
- Demanda de cliente, também: o trecho de injeção gerado pela ferramenta, onde ele vai no canal, os screenshots, os fatos de plataforma registrados e o endereço de homologação, se houve publicação.
- Última linha: como verificou.
- Fora: narrativa, lista de arquivos ou de fichas, próximos passos, defeito do trabalho (corrija antes).
- Aceitar a entrega aprova o que foi declarado.
- Corpo do commit: o porquê, não o que o diff mostra.
