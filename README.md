# Solo Up Sky

Jogo 2D de fantasia brutal em pixel art, em fase de fundação. Nome aprovado pelo Diretor em 2026-10-25 ([[ADR-003-Identidade-do-Projeto]]). **Engine aprovada: Bevy 0.20.0 + Rust stable** ([[ADR-001-Engine]]; migração do kit registrada em [[ADR-004-Migracao-Kit-Bevy]]); alvo WASM via `wasm32-unknown-unknown` e WebGL2.

## Kit inicial de agentes OpenCode + Obsidian

## O que foi entregue
8 agentes (`.opencode/agents/*.md`) reescritos para Bevy/Rust, `AGENTS.md` reescrito em merge, cofre Obsidian em `docs/`, 8 prompts de operação em `prompts/` (inclui 06-Configurar-Modelos e 07-Validar-WebAssembly).

## Instalar
1. Crie/abra um repositório Git local do jogo; faça backup de arquivos existentes.
2. Copie o **conteúdo** deste kit para a raiz do projeto, preservando `.opencode/agents/`.
3. Não sobrescreva AGENTS.md ou `.opencode` já existentes sem comparar e mesclar regras.
4. Abra a pasta `docs` como cofre no Obsidian.
5. Abra terminal **na raiz do projeto**, execute `opencode models` para obter IDs de modelos disponíveis.
6. **Concluído em 2026-10-25 (aprovado pelo Diretor):** o frontmatter de cada `.opencode/agents/*.md` já contém `model:` com o ID exato e `permissions:` no formato V2. Ver [[ADR-002-Agentes-e-Modelos]]. Sem o campo, o agente herdaria o modelo da sessão.
7. Execute `opencode agent list` (se disponível na versão instalada) e confira os oito agentes.
8. Inicie OpenCode, escolha `coordenador` e cole o conteúdo de `prompts/00-Iniciar-Coordenador.md` (sem `@coordenador` caso já esteja selecionado).

## Mapeamento aprovado em 2026-10-25 (ver [[ADR-002-Agentes-e-Modelos]])
| Agente | Modo | Modelo visível no menu | ID aplicado no frontmatter |
|---|---|---|---|
| coordenador (padrão) | primary | GLM-5.3-Flash Free | `opencode/glm-5.3-flash-free` |
| game-designer | subagent | DeepSeek V4.1 Flash Free | `opencode/deepseek-v4.1-flash-free` |
| narrativa | subagent | Flint 40B Free | `opencode/flint-40b-free` |
| arquiteto | subagent | GLM-5.3-Flash Free | `opencode/glm-5.3-flash-free` |
| gameplay | subagent | MiMo-V2.6-Flash Free | `opencode/mimo-v2.6-flash-free` |
| arte | subagent | Nemotron 3.5 Super VL Free | `opencode/nemotron-3.5-super-vl-free` |
| qa | subagent | Nemotron 3 Ultra Free | `opencode/nemotron-3-ultra-free` |
| documentador | subagent | Nemotron 3.5 Lightning Free | `opencode/nemotron-3.5-lightning-free` |

`default_agent` está definido como `coordenador` em `.opencode/opencode.json`. `Beam Free` e `Big Pickle` ficam para benchmarks. Modelos gratuitos podem ter limites ou mudar de disponibilidade; não presumir capacidades sem teste. Os prompts atualmente bloqueiam o QA de editar, e exigem confirmação para alterações de gameplay.

## Formato dos agentes
Os arquivos usam o formato nativo do OpenCode 2: frontmatter com `permissions:` (lista `action/resource/effect`) e `model:` por agente. Rodando no OpenCode 1, ajuste à sintaxe legada antes de usar; confira com `opencode --version` e `opencode debug agents`.

## Regras
- Documentos em `docs/` são propostas até o diretor aprová-los.
- Primeira execução é apenas análise/planejamento.
- Nunca fornecer aprovação humana automaticamente.
- Os dois arquivos originais enviados pelo usuário não foram modificados e devem ser guardados como fonte na pasta de referências.
- Game engine proibida: Godot. Stack aprovada: Bevy 0.20 + Rust; `Cargo.lock` versionado; validações `cargo fmt/check/clippy/test` e smoke test WASM antes de declarar pronto.

## Referência
Documentação oficial: https://opencode.ai/v2/docs/agents · Bevy 0.20: https://bevy.org/news/bevy-0-20/ · Avian2D: https://docs.rs/crate/avian2d/0.8.0
