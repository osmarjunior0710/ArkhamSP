# ArkhamSP

RPG com uma IA que narra, chamada **MestrIA** (sem gênero: sem artigo, sem "a mestra" nem "o mestre"). Fase atual: protótipo como Artifact do Claude.
Jogadores por enquanto: o Osmar e a esposa.

O Osmar é **QA / Game Designer, não é dev**. Ele não revisa código.

## Regras de trabalho

1. **Uma parte por vez.** Nada de construir várias coisas de uma vez.
2. **Todo trabalho começa num ticket do Jira** (projeto `AT`, site `osmarmelojunior.atlassian.net`). Sem ticket, não começa.
   O projeto se chamava `AHSP` até 2026-11-05: chaves antigas `AHSP-N` são as mesmas `AT-N`.
   O Osmar pretende criar um projeto novo no modelo Kanban; quando isso acontecer, atualizar a sigla aqui.
3. **Antes de começar, confirmar com o Osmar** qual ticket será feito.
4. **Decisões tomadas ficam em `docs/decisoes.md`**, para não serem rediscutidas.
5. **Na dúvida, perguntar uma coisa de cada vez**, de forma simples e sem jargão técnico.
6. **O Osmar dá a direção, o Claude propõe o caminho.** O Osmar diz o que quer ver e sentir no jogo.
   As decisões técnicas são do Claude, mas ele sempre apresenta as **opções viáveis** em linguagem simples
   (o que cada uma entrega, o custo/esforço e o que se perde) e **recomenda uma**. O Osmar escolhe.

## Jira como histórico (backtrack)

Os tickets são a **memória do projeto**. Tudo o que for criado ou alterado fica registrado neles,
de forma que dê para reconstruir o raciocínio depois só lendo o Jira.

- **Descrição:** objetivo, critérios de aceite e o **desenho técnico** do que será feito.
- **Comentários:** o histórico do trabalho: o que foi feito, decisões no caminho, problemas encontrados.
- Registrar sempre os **detalhes técnicos criados ou alterados**, por exemplo:
  - coleções e documentos do banco, com seus **campos, tipos e valores possíveis**;
  - atributos de personagem, regras de dados, fórmulas;
  - arquivos, links do Artifact e versões publicadas;
  - textos de instrução (prompt) dados à MestrIA;
  - nomes de funções/telas importantes e onde ficam.
- **Ligar tickets relacionados** (ex.: "depende de", "relacionado a") e citar a chave (`AT-N`) nos commits.
- Antes de mexer em algo existente, **ler os tickets anteriores** sobre aquilo.

## Hierarquia no Jira

```
Épico            → uma entrega grande / uma "vertical" do produto (ex.: Ficha de personagem, MestrIA)
 ├─ Tarefa       → uma parte entregável do épico
 │   └─ Subtask  → um passo da tarefa. Subtask com label `bug` = "subbug": bug achado testando ESSA tarefa
 └─ Bug          → bug em algo maior ou já concluído; fica no épico e é ligado à tarefa de origem
```

**Antes de qualquer trabalho novo:**
1. Procurar os épicos existentes (`project = AT AND issuetype = Epic`).
2. Se algum parece servir, **perguntar ao Osmar** se aquele épico cobre o assunto ou se é preciso um novo.
3. Se não houver épico, propor um novo.
4. Quebrar o épico em tarefas (e as tarefas em subtasks, quando fizer sentido).

**Todo épico tem na descrição:**
- **Propósito**: por que ele existe e o que entrega para o jogador;
- **O que entra / o que não entra**;
- **Contexto e dependências** com outros épicos.

Antes de decidir algo numa tarefa, **subir na hierarquia** (ler o épico) e **olhar os tickets vizinhos**
(outras tarefas do mesmo épico e épicos relacionados) para manter tudo coerente.

O Claude mantém os status atualizados: o épico fica **Em andamento** enquanto alguma tarefa dele estiver aberta.

## Padrões de UI/UX

O arquivo `docs/padroes-ui.md` é o catálogo de padrões de interface e funcionalidade.

- **Antes de qualquer trabalho de tela ou funcionalidade:** consultar o arquivo. Se já existe um padrão para a
  mesma ideia (ex.: "magias" e "pactos" são ambos recursos contáveis), **reutilizar**. Na dúvida se é o mesmo
  padrão ou um novo, perguntar ao Osmar.
- **Ao criar algo novo de UI:** registrar o padrão no arquivo, no mesmo ticket.
- **Labels do Jira:** cada padrão tem uma label `ui-<nome>` (kebab-case, sem acento), aplicada a todo ticket que
  cria, usa ou altera o padrão. Únicas labels permitidas: `ui-*` (registradas no arquivo) e `bug`.
- **Para mudar um padrão:** buscar `project = AT AND labels = ui-<nome>` e refatorar todos os usos juntos.

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

## Teste antes de entregar (celular e computador)

Toda entrega que aparece na tela passa por teste nos dois formatos, antes de ir para Em análise:
- **Celular:** 390 × 844 (formato de referência do projeto).
- **Computador:** 1280 × 800.
- Conferir: nada importante escondido atrás de barras fixas, sem rolagem lateral, botões alcançáveis com o polegar.
- O roteiro de teste para o Osmar sempre inclui passos no celular.
