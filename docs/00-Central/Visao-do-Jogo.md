---
tipo: visao
status: briefing-original-resumido
fonte: Contexto Geral do Jogo.md
---
# Visão do jogo
> **Resumo derivado do briefing original; não substitui o documento original.**

- **Nome do jogo: Solo Up Sky** (definido pelo Diretor em 2026-10-25 — ver [[ADR-003-Identidade-do-Projeto]]).
- Jogo de ação 2D pixel art detalhado, fantasia brutal, iluminação vibrante, câmera seguindo personagem, cutscenes de bosses e diálogos importantes.
- Referências de ritmo/visual: Dead Cells, Astral Ascent. Runs com fases/mundos aleatórios e situações narrativas de decisão.
- Modo história: Nicolas Kirsch Mazzini, brasileiro de 17 anos (1,85 m, 131 kg, óculos, cabelo cacheado curto, pele branca), transportado ao corpo do demi-humano Gratrels Silvernard (touro/lobo, 2,10 m, 147 kg, berserker, 15 anos).
- Modo personalizado: o jogador escolhe o nome, a aparência e tudo do próprio personagem (definido pelo Diretor em 2026-10-25).
- Progressão: níveis do personagem, atributos, skills com níveis, artefatos em baús; qualidades **Comum, Incomum, Raro, Diferente, Lendário**.
- Item Diferente: existe apenas um no jogo; Lendário: reliquia de herói ou figura histórica.
- Dez raças: Humanos, Elfos, Goblins, Dragonatos, DemiHumanos, Orcs, Warforged, Halflings, Gigantes, Etherean.
- Cada raça: História, Biologia, Atributos Base, Fraquezas, Qualidades, Aparência masculina e feminina detalhada. Híbridos coerentes.
- Objetivos técnicos: fluidez, manutenção simples e exportação WebAssembly.

## Pendências de decisão
- Identidade visual e nome da build/repositório remoto (nome do jogo já definido: **Solo Up Sky**).
- Combate e câmera detalhados; combate/escopo da primeira versão.
- Como o item "Diferente" é único: global em todas as runs, por save ou por campanha?
- Regras de geração procedural e escolhas persistentes.
- Engine aprovada: **Bevy 0.20 + Rust stable** (ver [[ADR-001-Engine]]); validação WASM/WebGL2 pendente.

## Conexões
[[Roadmap]] · [[Backlog-Sprint-0]] · [[ADR-001-Engine]]
