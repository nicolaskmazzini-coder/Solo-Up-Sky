# AGENTS.md — Regras do Estúdio — Solo Up Sky (Bevy + Rust)

## Hierarquia de autoridade
1. Diretor humano (usuário): autoridade final sobre universo, escopo, jogabilidade, arquitetura, releases e integração.
2. Documentos aprovados em `docs/`: fonte de verdade; conflitos são registrados, nunca resolvidos silenciosamente.
3. `docs/00-Central/Visao-do-Jogo.md`: resumo derivado do briefing original; os originais enviados pelo Diretor ficam ao lado como fonte.
4. Coordenador: planeja e delega; não substitui aprovação humana.
Fonte da verdade na execução: Visão do Jogo → ADRs aprovadas (`docs/03-Desenvolvimento/`) → backlog (`docs/05-Planejamento/`) → implementação verificada no repositório. Em conflito, interromper e pedir decisão humana, sem inventar lore nem corrigir silenciosamente documentos.

## Projeto e restrições
Jogo **Solo Up Sky**: roguelite 2D de fantasia brutal em pixel art detalhada, iluminação vibrante, câmera lateral acompanhando o protagonista, combate ágil, fases procedurais com seed, narrativa por escolhas, modos história/personalizado. Referências de sensação e apresentação: Dead Cells e Astral Ascent; **não copiar** recursos, código, personagens ou arte.

Modo história: Nicolas Kirsch Mazzini (brasileiro, 17 anos) no corpo do demi-humano Gratrels Silvernard (touro/lobo, berserker, 15 anos). **Modo personalizado: o jogador define o nome e tudo do próprio personagem.** Preservar dados como descritos no briefing; ambiguidades viram perguntas, não invenção de cânone.

Raças previstas (10): Humanos, Elfos, Goblins, Dragonatos, DemiHumanos, Orcs, Warforged, Halflings, Gigantes e Etherean. Cada uma exige história, biologia, atributos base, fraquezas, qualidades e aparência masculina/feminina detalhada; híbridos somente quando coerentes e aprovados.

Qualidades de itens **exatamente como no briefing**: Comum, Incomum, Raro, Diferente (único no jogo), Lendário (relíquia histórica). Não renomear ou alterar definições sem aprovação.

## Stack (aprovada — ver ADR-001)
- **Bevy 0.20.0 + Rust stable** (`rust-toolchain.toml` fixado após inspeção local); arquitetura ECS modular, um crate no início, módulos por domínio.
- **Avian2D 0.8.0** para física, adicionada após smoke test; Tiled + bevy_ecs_tiled 0.14.0 + bevy_ecs_tilemap 0.20.0 ficam **opcionais** até haver necessidade de mapas; LDtk/`bevy_ecs_ldtk` excluído por incompatibilidade de versão.
- Dados com Serde (JSON/RON); geração procedural com seed; **`Cargo.lock` versionado**.
- Alvo WASM: `wasm32-unknown-unknown` com **WebGL2** como primeiro caminho; validação de exportação web deve acontecer cedo.
- **Proibido**: Godot/GDScript, APIs de versões antigas do Bevy, múltiplas engines, dependências não avaliadas, execução arbitrária de código externo, MCP de terceiros sem revisão de segurança.

## Política de execução
- Por padrão, **somente planejar**. Editar código do jogo apenas quando o Diretor autorizar explicitamente tarefa e escopo.
- A autorização de uma tarefa não autoriza mudanças no restante do projeto.
- Antes de alterar: ler requisitos, arquivos afetados, branch e `git status`; registrar riscos.
- **Nunca executar `git push`, merge, rebase destrutivo, reset hard, exclusões em massa, deploy ou publicação sem autorização separada.** Branch curta por tarefa quando autorizado.
- Nunca pedir/registrar tokens, senhas, chaves privadas ou dados secretos em notas.
- Mudanças pequenas, modulares, documentadas e testáveis; dependências sem justificativa são negadas.
- Agentes **não são fonte de verdade** sobre compilação: testes, `Cargo` e logs são.

## Fluxo obrigatório
1. Receber ID da tarefa, escopo, critérios de aceite e arquivos permitidos.
2. Produzir mini-plano: arquivos afetados, dependências, incertezas e riscos.
3. Obter aprovação explícita do Diretor antes de implementar.
4. Implementar apenas o escopo aprovado, em branch curta quando autorizado.
5. Verificações obrigatórias, quando couberem, executadas de fato e com saída registrada: `cargo fmt --all -- --check`, `cargo check`, `cargo clippy --all-targets -- -D warnings`, `cargo test` e `cargo check --target wasm32-unknown-unknown` (quando o alvo estiver instalado/configurado). Nunca inventar saídas.
6. Revisão por @qa independente das mudanças de código e config relevante.
7. Atualizar nota Obsidian de tarefa e diário (`docs/07-Diario/`) com evidências.
8. Entregar para aceite humano. **Concluído** somente após aceite registrado.

## Qualidade de jogabilidade
- Separar movimento, hitboxes/hurtboxes, dano e VFX; movimento e câmera responsivos; `FixedUpdate` onde apropriado; evitar alocações por frame.
- Colisões testadas; **seed de run reproduzível**.
- Pixel art com `nearest-neighbor`, resolução interna consistente; medir FPS e custo de efeitos, com fallback para limites do WebGL2.

## Obsidian
`docs/` é o cofre Obsidian: Markdown, links `[[Nota]]`, frontmatter YAML, nomes previsíveis, notas pequenas e índice MOC. Uma fonte de verdade por decisão; referenciar em vez de duplicar. Notas de decisão recebem IDs `ADR-xxx`; tarefas, `GAME-xxx`. Diário datado em `docs/07-Diario/`. Jamais sobrescrever conteúdo de lore aprovado sem solicitação; agentes não alteram decisões aprovadas e não inventam evidências.

## Definition of Done
Critérios de aceite atendidos + testes/cargo checks executados e registrados + documentação atualizada + QA independente + aprovação humana explícita. Sem os cinco, status é AGUARDANDO APROVAÇÃO ou BLOQUEADO.

## Formato mínimo de relatório de qualquer agente
- Tarefa / responsável / status: PROPOSTO | EM ANDAMENTO | BLOQUEADO | AGUARDANDO APROVAÇÃO | APROVADO
- Objetivo e escopo
- Arquivos lidos e alterados
- Decisões tomadas e premissas (identificar hipóteses)
- Evidências (comandos, saídas, resultados reais; marcar NÃO EXECUTADO quando for o caso)
- Riscos e regressões possíveis
- Pendências e questões para o Diretor
- Próxima ação recomendada
