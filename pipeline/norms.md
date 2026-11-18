# Normas

Obrigação ou proibição verificável no código. `Checagem: prevista` quer dizer que a ferramenta ainda não existe: até lá, garantem a conferência e a revisão.

Todas provisórias: `pipeline/records.md › Decisões`, D3 e D4.

Norma nova segue este formato, com o próximo ID; ID removido não volta:

```markdown
## N<n> · <nome curto>

<A obrigação ou proibição.>

- Porque: <o motivo>
- Vale para: <o alcance, quando não é óbvio>
- Exceto: <o caso permitido>
- Checagem: <a ferramenta que a verifica, ou `prevista: <qual>`>
```

## N1 · Idioma

Identificadores e nomes de arquivo e de pasta em inglês. Texto para pessoas e agentes (documentação, pipeline, mensagem de commit) em português do Brasil.

- Porque: um idioma por destino. O ecossistema é em inglês; o time lê em português.
- Exceto: nome imposto por ferramenta ou contrato externo; slug de cliente; texto exibido no canal, que vem do pedido.
- Checagem: nenhuma automática para o idioma. Garante a revisão.

## N2 · Ordem alfabética

Ordene alfabeticamente o que não tem ordem com significado: imports, exports, propriedades, chaves, membros de listas e de uniões, declarações independentes.

- Porque: qualquer item se acha sem procurar, e o diff mostra só o que mudou.
- Vale para: código e configuração autorais.
- Exceto: ordem de execução; dependência de inicialização; precedência, como a cascata de estilos; ordem de exibição; ordem que a ferramenta exige.
- Checagem: prevista: regra de ordenação no lint, com correção automática.

## N3 · Sem comentários

Não escreva comentários no código: de linha, de bloco, de documentação nem código comentado.

- Porque: nomes e estrutura explicam o código. O que faltar mora na documentação.
- Checagem: prevista: regra de lint que rejeita comentário.

## N4 · Import por alias

Import interno usa o alias da área. Caminho relativo é proibido.

- Porque: o import não depende de onde está o arquivo, e mover um arquivo não quebra os vizinhos.
- Vale para: import estático, reexportação e `import()`. Pacote externo segue pelo nome.
- Checagem: prevista: regra de lint que rejeita import relativo.

## N5 · Tipagem estrita

Todo código é TypeScript no modo estrito. `any` explícito e diretiva que suprime erro de tipo são proibidos.

- Porque: o erro de tipo aparece na verificação, não no canal do cliente.
- Checagem: prevista: checagem de tipos no modo estrito e regra de lint contra `any` explícito e supressão, na verificação, antes do commit e no CI.

## N6 · Cor por token

Cor vem de token de design. Literal de cor (hex, `rgb`, `hsl`, nome) fora da definição dos tokens é proibido.

- Porque: a cor da marca do cliente muda num lugar só, e nada diverge entre scripts.
- Vale para: código e estilos.
- Exceto: palavra-chave sem cor própria: `currentColor`, `inherit`, `transparent`.
- Checagem: prevista: regra de lint de código e de estilos que rejeita literal de cor fora da definição dos tokens.

## N7 · Mensagem de commit

Conventional Commits. Mudança no script de um cliente leva o slug dele como escopo, e o slug é de um cliente existente.

- Porque: o histórico se filtra por tipo e por cliente.
- Checagem: prevista: validação da mensagem antes do commit e no CI.
