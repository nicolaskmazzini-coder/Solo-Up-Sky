# AGENTS.md — Diretrizes obrigatórias do jogo

## Hierarquia de autoridade
1. Diretor humano (usuário): autoridade final sobre universo, escopo, jogabilidade, arquitetura, releases e integração.
2. Documentos aprovados em `docs/`: fonte de verdade; conflitos são registrados, nunca resolvidos silenciosamente.
3. `docs/00-Central/Visao-do-Jogo.md`: resumo dos requisitos originais, sujeito à aprovação.
4. Coordenador: planeja e delega; não substitui aprovação humana.

## Projeto e restrições
Jogo 2D de fantasia brutal em pixel art detalhada, com iluminação vibrante, câmera lateral acompanhando o protagonista, combate ágil, fases/rotas procedurais, narrativa por escolhas, modos história/personalizado, progressão por níveis, habilidades e artefatos. Referências de sensação e apresentação: Dead Cells e Astral Ascent; **não copiar** recursos, código, personagens ou arte.

O modo história acompanha Nicolas Kirsch Mazzini (brasileiro, 17 anos), transportado para o corpo do demi-humano Gratrels Silvernard (híbrido touro/lobo, berserker, 15 anos). Preservar dados como descritos no briefing; tratar ambiguidades como perguntas, não inventar cânone.

Raças previstas: Humanos, Elfos, Goblins, Dragonatos, DemiHumanos, Orcs, Warforged, Halflings, Gigantes e Etherean. Cada uma exige história, biologia, atributos base, fraquezas, qualidades e aparência masculina/feminina detalhada; híbridos somente quando coerentes e aprovados.

Qualidades de itens **exatamente como no briefing**: Comum, Incomum, Raro, Diferente (único no jogo), Lendário (relíquia histórica). Não renomear ou alterar as definições sem aprovação.

Tecnologia **proposta, não aprovada**: Godot 4, GDScript e renderizador Compatibility; exportação WebAssembly deve ser validada cedo. Priorizar simplicidade, performance, portabilidade e manutenção.

## Política de execução
- Por padrão, **somente planejar**. Editar código do jogo apenas quando o Diretor autorizar explicitamente tarefa e escopo.
- A autorização de uma tarefa não autoriza mudanças no restante do projeto.
- Antes de alterar, ler requisitos, arquivos afetados, branch e `git status`; registrar riscos.
- Não executar `git push`, merge, rebase destrutivo, reset hard, exclusões em massa, deploy ou publicação sem autorização separada.
- Nunca pedir/registrar tokens, senhas, chaves privadas ou dados secretos em notas.
- Criar branch por tarefa quando autorizado; nunca fazer commits automáticos sem política aprovada.
- Preferir mudanças pequenas, modulares, documentadas e testáveis; evitar dependências sem justificativa.
- Não afirmar execução de teste que não ocorreu. Exibir comandos, resultados e limitações.
- Os agentes não podem criar ou alterar decisões de cânone já aprovadas por conta própria.
- Divergências entre documentos e código devem virar registros `PENDENTE`.

## Fluxo obrigatório
1. Receber ID da tarefa, escopo, critérios de aceite e arquivos permitidos.
2. Propor plano e identificar dependências e incertezas.
3. Obter aprovação explícita do Diretor antes de implementar.
4. Implementar apenas escopo aprovado.
5. Executar verificações disponíveis e revisão por QA independente.
6. Atualizar nota Obsidian de tarefa e relatório de evidências.
7. Entregar para aceite humano. **Concluído** somente após aceite registrado.

## Formato de relatório de qualquer agente
- Tarefa / responsável / status: PROPOSTO | EM ANDAMENTO | BLOQUEADO | AGUARDANDO APROVAÇÃO | APROVADO
- Objetivo e escopo
- Arquivos lidos e alterados
- Decisões tomadas e premissas (identificar hipóteses)
- Evidências (comandos, testes, prints quando disponíveis)
- Riscos e regressões possíveis
- Pendências e questões para o Diretor
- Próxima ação recomendada

## Obsidian
`docs/` é o cofre Obsidian. Usar Markdown, links `[[Nota]]`, frontmatter YAML e nomes previsíveis. Uma fonte de verdade por decisão; referenciar em vez de duplicar. Notas de decisão recebem IDs ADR-xxx; tarefas, GAME-xxx. Jamais sobrescrever conteúdo de lore aprovado sem solicitação.

## Definition of Done
Critérios de aceite atendidos + testes executados e registrados + documentação atualizada + QA independente + aprovação humana explícita. Sem os cinco, status é AGUARDANDO APROVAÇÃO ou BLOQUEADO.
