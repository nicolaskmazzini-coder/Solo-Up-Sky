# Solo Up Sky

Jogo 2D de fantasia brutal em pixel art, em fase de fundação (documentação, regras e agentes). Nome aprovado pelo Diretor em 2026-10-25 — ver [[ADR-003-Identidade-do-Projeto]].

## Kit inicial de agentes OpenCode + Obsidian

## O que foi entregue
8 agentes (`.opencode/agents/*.md`), `AGENTS.md`, cofre Obsidian em `docs/`, 6 prompts de operação em `prompts/`.

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

## Atenção: versão do OpenCode
Este kit usa formato Markdown **legado/documentado em opencode.ai/docs/agents** com `permission:` e `mode:`. Se você usar uma variante do OpenCode que espera o formato V2 com `permissions:` (lista), adapte o frontmatter conforme documentação da versão instalada. A compatibilidade exata exige validação local.

## Regras
- Documentos em `docs/` são propostas até o diretor aprová-los.
- Primeira execução é apenas análise/planejamento.
- Nunca fornecer aprovação humana automaticamente.
- Os dois arquivos originais enviados pelo usuário não foram modificados e devem ser guardados como fonte na pasta de referências.

## Referência
Documentação oficial: https://opencode.ai/docs/agents
