---
tipo: decisao
id: ADR-004
status: aprovada-direcao-pendente-validacao
aprovado_por: Diretor humano
data: 2026-10-25
relacionados: ["ADR-001", "ADR-002", "ADR-003", "Backlog-Sprint-0", "Roadmap"]
---

# ADR-004 — Migração do kit Bevy/Rust (merge)

## Contexto
O Diretor adicionou `kit-bevy-rust-opencode.zip` com novas decisões: troca de engine, agentes reescritos, roadmap e Sprint 0 voltados a Rust/Bevy e dois prompts novos (06-Configurar-Modelos, 07-Validar-WebAssembly). O kit dizia para substituir tudo sem mesclar agentes antigos; o Diretor ordenou **executar um merge inteligente** com o conteúdo já aprovado neste repositório.

## Decisões aprovadas pelo Diretor (2026-10-25)
1. **Troca de engine confirmada oficialmente: Godot descartado; Bevy 0.20 + Rust** ([[ADR-001-Engine]]). A proposta Godot nunca foi implementada e foi arquivada em `docs/03-Desenvolvimento/Arquivo/ADR-001-Godot-proposta-arquivada.md` (cópia histórica, não canônica).
2. **Substituição autorizada** de agentes, roadmap, backlog, plano de testes e prompts pelo conteúdo do kit.
3. **Sobreposição de poder feita da melhor forma**: nos `.opencode/agents/*.md` ficou o **corpo e a descrição do kit**, com o **frontmatter deste repositório** — pin de `model:` aprovado em [[ADR-002-Agentes-e-Modelos]] e regras de permissão mais estritas (subagentes negados nos especialistas; `coordenador` com lista fechada de subagentes e `gameplay` dependendo de confirmação). `default_agent: coordenador` permanece em `.opencode/opencode.json`.
3.1. **`Visao-do-Jogo.md` NÃO foi reescrita**: a versão do kit é mais curta e apagaria decisões aprovadas (nome do jogo, modo personalizado, pendências). O corpo anterior permanece; o kit só trouxe redação condensada, sem informação nova de cânone.
4. **Crate Rust nascerá em `game/`** (não na raiz do repositório), mantendo o layout decidido em [[ADR-002-Agentes-e-Modelos]]. O projeto (Cargo.toml) só será criado junto à tarefa GAME-003, após aprovação da Sprint 0.
5. **`rustup target add wasm32-unknown-unknown` autorizado e executado** (ver evidências).
6. **`AGENTS.md` reescrito em merge**, combinando hierarquia de autoridade, política de execução, Obsidian e Definition of Done do documento anterior com a Stack, o rito de verificação por `cargo` e as regras de qualidade de jogabilidade do kit.

## Merges executados
| Item | Como foi incorporado |
|---|---|
| `.opencode/agents/*.md` (8) | corpo/descrição do kit + `model:` + `permissions:` deste repo |
| `prompts/00..05` | substituídos pelos do kit; **novos**: `06-Configurar-Modelos.md`, `07-Validar-WebAssembly.md` |
| `docs/03-Desenvolvimento/ADR-001-Engine.md` | substituída por Bevy + registro da troca; proposta Godot arquivada |
| `docs/05-Planejamento/Roadmap.md` | corpo do kit + frontmatter local |
| `docs/05-Planejamento/Backlog-Sprint-0.md` | corpo do kit (8 tarefas) + frontmatter local |
| `docs/06-Testes/Plano-de-Testes-Inicial.md` | plano de QA Rust do kit + frontmatter local |
| `docs/00-Central/Contexto Geral do Jogo.md` e `Detalhes.md` | movidos de `docs/` para `00-Central/` (wikilinks não dependem de caminho) |
| `AGENTS.md` | reescrito em merge (única fonte de verdade) |
| `README.md` | atualizado com a stack aprovada |
| `.gitignore` | itens Godot trocados por blocos Rust (`game/target/`, `game/dist/`) |
| `game/README.md` | atualizado para o novo papel da pasta (crate Bevy) |
| `kit-bevy-rust-opencode.zip` | **excluído** após o merge, conforme pedido |

## Evidências
- Antes: `rustup target list --installed` = `x86_64-pc-windows-msvc` apenas. Depois do `rustup target add wasm32-unknown-unknown`: verificar no relatório da sessão.
- crates.io em 2026-10-25: bevy 0.20.0 (2026-10-08) · avian2d 0.8.0 (requer `bevy ^0.20`) · bevy_ecs_tilemap 0.20.0 · bevy_ecs_tiled já com 0.15.0 publicada (2026-10-24).
- Pacote extraído em `%TEMP%\opencode\kit-bevy-rust-extract\` como referência de merge; removido no fim com o próprio zip.
- Local: `rustc 1.99.0 (2026-09-28)`, `cargo 1.99.0`, `rustup` presentes.

## Pendências e riscos
- **NÃO VALIDADO ainda**: build nativo, smoke test WASM/WebGL2, criação do crate (GAME-003). Isso é conteúdo da Sprint 0, com revisão do @qa.
- Confirmar com @arquiteto por que o kit fixou `bevy_ecs_tiled 0.14.0` quando a 0.15.0 já existe — antes de adicionar mapas.
- Curva de aprendizado de Rust + Bevy + ECS para um estúdio iniciante: custo de tempo assumido pelo Diretor ao decidir a troca.
- Binário WASM de Bevy é grande (MB a dezenas de MB): exigir otimização e medição cedo.
- Os prompts do kit referenciam `docs/07-Diario/` (inexistente até o @documentador iniciar um diário).

## Conexões
[[ADR-001-Engine]] · [[ADR-002-Agentes-e-Modelos]] · [[ADR-003-Identidade-do-Projeto]] · [[Backlog-Sprint-0]] · [[Roadmap]]
