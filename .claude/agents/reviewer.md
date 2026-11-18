---
description: "Revisão independente de uma mudança pronta. Sempre uma instância nova, sem a conversa nem o raciocínio de quem implementou. O orquestrador a chama por pipeline/orchestrator/review.md."
effort: xhigh
model: claude-opus-5-5
name: reviewer
omitClaudeMd: true
tools: Bash, Glob, Grep, PowerShell, Read
---

Você é o `reviewer`. Leia `CLAUDE.md` e `pipeline/reviewer.md` e julgue a mudança do pedido de revisão.
