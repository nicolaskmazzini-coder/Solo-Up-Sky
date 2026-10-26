---
tipo: adr
status: aprovada-direcao-pendente-validacao
data: 2026-10-25
---
# ADR-001 — Bevy + Rust
## Contexto
Diretor descartou Godot por preferência e adotou Bevy + Rust. Requisitos: game 2D plataforma pixel art, performance, manutenção, WASM, agentes OpenCode.
## Decisão
Bevy 0.20.0 com Rust Stable, arquitetura ECS modular; começar com um crate e módulos Rust. Avian2D 0.8.0 para física; quando necessário, Tiled + bevy_ecs_tiled 0.14.0 e bevy_ecs_tilemap 0.20.0. WebGL2 como primeiro caminho WASM. Dados Serde JSON/RON. Geração procedural com seed.
## Condições
Validar cargo check/test e browser smoke antes de declarar pronto; validar APIs específicas por versão e pinned Cargo.lock. Ferramentas opcionais não são obrigatórias. O LDtk/bevy_ecs_ldtk 0.15 é Bevy 0.19 e não entra agora.
## Alternativas
Godot (descartada pelo diretor), Defold e Macroquad (não adotadas).
## Links técnicos
- https://bevy.org/news/bevy-0-20/
- https://docs.rs/crate/avian2d/0.8.0
- https://docs.rs/crate/bevy_ecs_tiled/0.14.0
- https://docs.rs/crate/bevy_ecs_tilemap/0.20.0

## Registro
- **2026-10-25:** direção Bevy + Rust confirmada oficialmente pelo Diretor. Proposta Godot anterior, nunca implementada, arquivada em [[ADR-001-Godot-proposta-arquivada]]; a migração completa está registrada em [[ADR-004-Migracao-Kit-Bevy]].
- Validação pendente antes de declarar pronto: build nativo, target `wasm32-unknown-unknown`, `cargo check/test/clippy` e browser smoke test (WebGL2).
- Verificado em 2026-10-25 no crates.io: bevy 0.20.0, avian2d 0.8.0 (depende de `bevy ^0.20`), bevy_ecs_tilemap 0.20.0 são versões reais e compatíveis; bevy_ecs_tiled já tem 0.15.0 publicada — confirmar com @arquiteto por que o kit pinou 0.14.0 antes de adicionar mapas.

## Conexões
[[Visao-do-Jogo]] · [[Roadmap]] · [[Backlog-Sprint-0]] · [[ADR-004-Migracao-Kit-Bevy]]
