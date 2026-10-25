---
tipo: decisao
id: ADR-003
status: aprovado
aprovado: true
aprovado_por: Diretor humano
data: 2026-10-25
relacionados: ["ADR-001", "ADR-002", "Visao-do-Jogo"]
---

# ADR-003 — Identidade do projeto, cofre e modo personalizado

## Contexto
"Solo Up Sky" era apenas o nome da pasta de trabalho; o título do jogo constava como pendência na [[Visao-do-Jogo]]. O cofre Obsidian estava em `Docs/` (maiúsculo) enquanto `AGENTS.md` e os 6 prompts de operação referenciam `docs/` — divergência que quebra em Git/Linux/CI. O modo personalizado só estava descrito como "criar próprio personagem", sem dizer quem define nome e demais escolhas.

## Decisões
1. **Nome do jogo: Solo Up Sky** (aprovado em 2026-10-25).
2. **Cofre padronizado em `docs/`** (minúsculo). A pasta foi renomeada de `Docs/` para `docs/`; `.gitignore` e [[ADR-002-Agentes-e-Modelos]] atualizados. `AGENTS.md` e `prompts/` já usavam `docs/`, então nenhum deles precisou mudar.
3. **Modo personalizado: o jogador define o nome e tudo do próprio personagem** — aparência e demais escolhas de criação. O modo história continua fixo em Nicolas Kirsch Mazzini → Gratrels Silvernard.
4. **Nome da build e do repositório remoto: pendentes**, a serem informados pelo Diretor.

## Fora de escopo desta decisão
- Quais raças/atributos estarão disponíveis no modo personalizado, orçamento de pontos e limites de criação: depende do desenho de progressão (game-designer) e de aprovação posterior.
- Identidade visual, logotipo e tipografia.
- Engine (permanece em [[ADR-001-Engine]], `proposta`).

## Evidências
- `Rename-Item Docs → docs` executado; `Get-ChildItem -Directory` lista `docs`.
- Busca por `Docs/` no repositório: restavam `.gitignore` e ADR-002, ambos corrigidos.
- `docs/00-Central/Visao-do-Jogo.md` atualizado com nome do jogo e regra do modo personalizado.

## Consequências
- Links internos do Obsidian (`[[Nota]]`) não dependem do caminho, então a renomeação não quebrou wikilinks.
- O título do jogo deixa de ser pendência; a pendência restante é identidade visual e nomes de build/repositório.

## Conexões
[[ADR-001-Engine]] · [[ADR-002-Agentes-e-Modelos]] · [[Visao-do-Jogo]] · [[Roadmap]]
