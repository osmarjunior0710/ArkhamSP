# ArkhamSP

RPG com IA mestra. Fase atual: protótipo como Artifact do Claude.
Jogadores por enquanto: o Osmar e a esposa.

O Osmar é **QA / Game Designer, não é dev**. Ele não revisa código.

## Regras de trabalho

1. **Uma parte por vez.** Nada de construir várias coisas de uma vez.
2. **Todo trabalho começa num ticket do Jira** (projeto `AHSP`, site `osmarmelojunior.atlassian.net`). Sem ticket, não começa.
3. **Antes de começar, confirmar com o Osmar** qual ticket será feito.
4. **Decisões tomadas ficam em `docs/decisoes.md`**, para não serem rediscutidas.
5. **Na dúvida, perguntar uma coisa de cada vez**, de forma simples e sem jargão técnico.

## Fluxo dos tickets no Jira

| Status | Significado |
|---|---|
| Tarefas pendentes | Ainda não começou |
| Em andamento | O Claude está trabalhando nele |
| Em análise | O Claude terminou e está esperando a validação do Osmar |
| Concluído | Somente depois que o Osmar aprovar |

O Claude nunca move um ticket para **Concluído** por conta própria.

## Entrega de cada ticket

Ao terminar, mover o ticket para **Em análise** e comentar nele (e no chat):

- **Se a mudança não aparece na tela** (código interno, configuração, dados, arquivos de regra):
  avisar em linguagem simples **o que mudou, em qual lugar e por quê**, e o que isso afeta no jogo.
- **Se a mudança aparece na tela:** passar um **roteiro de teste** para o Osmar:
  - onde acessar (link);
  - passos numerados;
  - resultado esperado em cada passo;
  - casos de borda que vale testar (ex.: campo vazio, texto muito longo, dois jogadores ao mesmo tempo).
- Sempre listar o que ficou **pendente ou fora do escopo**.
