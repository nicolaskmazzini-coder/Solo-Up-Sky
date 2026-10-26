---
tipo: decisao
id: ADR-001-Godot-proposta-arquivada
status: arquivada
aprovado: false
arquivada_em: 2026-10-25
motivo: Diretor confirmou troca para Bevy + Rust (ver [[ADR-004-Migracao-Kit-Bevy]])
---
# ADR-001 (arquivada) — Engine inicial (proposta Godot)
## Contexto
Jogo 2D em pixel art com alta fluidez, manutenção acessível para iniciante e alvo navegador via WebAssembly.
## Proposta
Investigar **Godot 4 + GDScript + renderizador Compatibility**, sem confirmar definitivamente antes de uma prova de conceito exportada para web.
## Alternativas para comparar
Outras engines/frameworks 2D com exportação para web; exigir comparação de complexidade, ferramentas, performance e custo de manutenção.
## Prova obrigatória
Personagem com movimento, câmera, colisão e teste real no navegador, medindo FPS e verificando restrições de exportação.
## Decisão
**SUBSTITUÍDA em 2026-10-25:** o Diretor confirmou oficialmente a troca para **Bevy 0.20 + Rust** (decisão registrada em [[ADR-004-Migracao-Kit-Bevy]]). Esta nota permanece apenas como registro histórico e nunca foi implementada — não foi testada.

## Anotações originais
**PENDENTE DE APROVAÇÃO DO DIRETOR.**
