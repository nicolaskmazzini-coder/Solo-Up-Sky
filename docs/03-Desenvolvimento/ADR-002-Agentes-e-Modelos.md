---
tipo: decisao
id: ADR-002
status: aprovado
aprovado: true
aprovado_por: Diretor humano
data: 2026-10-25
relacionados: ["ADR-001", "Visao-do-Jogo", "Roadmap"]
---

# ADR-002 — Agentes, modelos e fundação do repositório

## Contexto
O kit de agentes já existia em `.opencode/agents/`, mas no formato V1 (legado) e **sem** o campo `model:`. Nesse estado cada agente herdava o modelo da sessão, e `temperature` era ignorado pelo OpenCode 2. O projeto também não tinha controle de versão.

## Decisão
1. Converter o frontmatter dos 8 agentes para o formato nativo V2 (`permissions:` como lista ordenada; `bash`→`shell`, `task`→`subagent`).
2. Fixar um modelo por agente, conforme mapeamento aprovado.
3. Definir `coordenador` como agente padrão de sessão.
4. Inicializar repositório Git local (branch `main`), `.gitignore` e a pasta `game/` (ainda vazia de código).

## Mapeamento aprovado
| Agente | Modo | Modelo | ID exato |
|---|---|---|---|
| coordenador (padrão) | primary | GLM-5.3-Flash Free | `opencode/glm-5.3-flash-free` |
| game-designer | subagent | DeepSeek V4.1 Flash Free | `opencode/deepseek-v4.1-flash-free` |
| narrativa | subagent | Flint 40B Free | `opencode/flint-40b-free` |
| arquiteto | subagent | GLM-5.3-Flash Free | `opencode/glm-5.3-flash-free` |
| gameplay | subagent | MiMo-V2.6-Flash Free | `opencode/mimo-v2.6-flash-free` |
| arte | subagent | Nemotron 3.5 Super VL Free | `opencode/nemotron-3.5-super-vl-free` |
| qa | subagent | Nemotron 3 Ultra Free | `opencode/nemotron-3-ultra-free` |
| documentador | subagent | Nemotron 3.5 Lightning Free | `opencode/nemotron-3.5-lightning-free` |

## Permissões resultantes
- Somente leitura (edição/shell/subagente negados): `arquiteto`, `arte`, `game-designer`, `narrativa`, `qa`.
- `documentador`: edição `ask`, shell negado.
- `gameplay`: edição e shell `ask`, sem subagentes.
- `coordenador`: edição e shell `ask`; subagentes apenas os 7 especialistas (`gameplay` exige confirmação).

## Evidências
- `opencode reload` → `Configuration reloaded`.
- `opencode debug agents` → os 8 agentes com `model` e `permissions` resolvidos.
- `opencode run --agent qa "Responda AGENTE-OK"` → resposta `AGENTE-OK`.
- `opencode models` → os 7 IDs usados existem no provedor `opencode`.
- `git init -b main` → repositório criado; `git status` lista os arquivos como não rastreados.
- Backup dos agentes originais (V1) em `%TEMP%\opencode\backup-agents-20261025\`.

## Consequências e riscos
- Modelos gratuitos podem ter limite de uso ou mudar de disponibilidade; troca é de uma linha por arquivo.
- `temperature` não é mais enviado ao modelo (o V2 não envia `request.body` de agente); controlar amostragem exigiria *variants* em `providers.models`.
- Para agentes `primary`, o modelo da sessão é escolhido separadamente; o `model:` vale para sessões-filhas de subagente.
- Nenhum commit foi feito: a política de commits automáticos ainda não foi aprovada.

## Pendências
- Cofre padronizado em `docs/` (minúsculo) em 2026-10-25 — ver [[ADR-003-Identidade-do-Projeto]].
- Nome do jogo definido: **Solo Up Sky** (2026-10-25). Nome da build e do repositório remoto ainda pendentes.
- Política de commits (mensagem, autoria, frequência) a aprovar.
- Validar na prática a capacidade de cada modelo (o teste cobriu carregamento, não qualidade).

## Conexões
[[ADR-001-Engine]] · [[Visao-do-Jogo]] · [[Roadmap]] · [[Backlog-Sprint-0]]
