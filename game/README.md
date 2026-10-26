# game/ — Crate Rust do jogo

Pasta reservada para o projeto Bevy. **Ainda vazia de propósito.**

- Engine aprovada: **Bevy 0.20.0 + Rust stable** (ver [[ADR-001-Engine]]; migração registrada em [[ADR-004-Migracao-Kit-Bevy]]).
- Nada de código ou `Cargo.toml` até o Diretor aprovar a tarefa GAME-003 do [[Backlog-Sprint-0]].
- O arquivo `Cargo.toml` nascerá na raiz desta pasta; `Cargo.lock` é **versionado** (builds reproducíveis).
- `target/` e `dist/` são ignorados pelo `.gitignore` da raiz.
- Antes de declarar pronto: `cargo fmt --check`, `cargo check`, `cargo clippy -D warnings`, `cargo test` e smoke test em navegador com `wasm32-unknown-unknown` + WebGL2 (ver [[Plano-de-Testes-Inicial]]).
