# Decisões do projeto

Registro das decisões já tomadas. Para mudar alguma, conversar com o Osmar antes.

| Data | Decisão | Motivo |
|---|---|---|
| 2026-11-04 | O protótipo será um **Artifact do Claude**, não um site próprio. | Dispensa chave de API e Firebase. A IA usa a conta Claude de cada jogador. |
| 2026-11-04 | Jogadores iniciais: **o Osmar e a esposa**. | Uso pessoal; o escopo fica pequeno. |
| 2026-11-04 | Site próprio (Firebase + API) fica para **depois**, se o protótipo fizer sentido. | Validar a diversão antes de investir. |
| 2026-11-04 | **Sem geração de imagens** no protótipo. | O Claude não gera imagens, e uma API de imagens teria custo à parte. |
| 2026-11-04 | Tracking no **Jira, projeto `AHSP`**. | Manter o foco entre sessões e projetos. |
| 2026-11-04 | O Osmar valida pelo que aparece na tela; o Claude explica o que é invisível e dá roteiro de teste para o que é visível. | O Osmar é QA/GD, não dev. |
| 2026-11-04 | Os tickets do Jira guardam o histórico técnico completo (campos, atributos, prompts, arquivos). | Permitir backtrack sem depender da memória do Claude. |
| 2026-11-04 | O Osmar dá direções; o Claude apresenta opções viáveis com recomendação e o Osmar escolhe. | Decisão técnica fica com quem entende o código, e a de produto com o Osmar. |
| 2026-11-04 | Hierarquia Épico > Tarefa/Bug > Subtask. "Subbug" = Subtask com label `bug`. | O Jira não tem um tipo "sub-bug"; a label mantém o bug preso à tarefa que está sendo testada. |
| 2026-11-04 | Todo trabalho começa procurando um épico existente; o Osmar confirma se ele serve ou se é preciso um novo. | Evitar épicos duplicados e manter o propósito claro. |
| 2026-11-04 | **Mundo:** horror cósmico em **São Paulo capital**. | Definição do Osmar (bloco 1 de escopo). |
| 2026-11-04 | **Referências:** franquia Arkham Horror (jogos e Arkham Horror Files). Nada 100% novo, nada 100% copiado. Nomes e personagens próprios. | Inspiração sem copiar propriedade da Fantasy Flight. Lovecraft é domínio público. |
| 2026-11-04 | **Narração:** mistura de Stephen King e Lovecraft, mais King do que Lovecraft. | Definição do Osmar (bloco 1 de escopo). |
| 2026-11-04 | **Ficha única** para todos os personagens. Campos a definir pelo Osmar. | Definição do Osmar (bloco 2 de escopo). |
| 2026-11-04 | **Três formas de criar personagem:** descrição livre (a IA preenche e pergunta o que faltar), perguntas rápidas ou perguntas completas. | Dar opção a quem quer agilidade e a quem quer detalhe. |
| 2026-11-04 | **Modo de mortalidade** escolhido no fim da criação: Mortal (morre), Semimortal (cai e volta com debuff), Imortal (desmaia e é salvo sem efeito colateral). | O jogador escolhe que tipo de história quer viver. |
| 2026-11-04 | ~~Dados iguais = crítico bom se passou, ruim se não passou.~~ Substituída em 2026-11-05. | |
| 2026-11-05 | **Dados:** 2d12, branco (Bênção) e preto (Mythos), + atributo contra a dificuldade. **Dados iguais = sempre crítico positivo** (sucesso automático). Não existe falha crítica. Demais resultados: sucesso, sucesso com deslize, falha com progresso, falha. | Decisão do Osmar. Igual ao Daggerheart nesse ponto. |
| 2026-11-04 | **Dificuldades:** 8 / 11 / 14 / 17 / 20 / 23 (de muito fácil a quase impossível). Balanceamento aprovado como ponto de partida, ajustado pela história e pela evolução dos personagens. | Proporções levemente pessimistas, como em Arkham, sem exagero. |
| 2026-11-05 | **Visual final dos dados = prova de conceito v2** (`poc/dados-3d.html`): d12 3D (Three.js) com física real (cannon.js), batendo, esbarrando e quicando; resultado sorteado antes e garantido pela troca de números das faces; som de batida com botão de silenciar. | Aprovado pelo Osmar: "é o que eu quero no final". Confirmado que funciona dentro do Artifact. |
| 2026-11-05 | **Mestra narrativa:** só pede rolagem quando o resultado importa. Regras finas (máximo de rolagens por situação, quando rola, tentativas repetidas) ficam para depois. | Jogo mais narrativo. |
| 2026-11-05 | **A mestra decide o que rolar** (atributo e dificuldade) e adapta quando o jogador propõe uma solução diferente que faz sentido. A rolagem **acontece automaticamente**; o jogador não é chamado a rolar. | Fluidez da narração. |
| 2026-11-05 | **Limites de conteúdo por jogador** (horror, gore, violência…), definidos na criação do personagem; a mestra se adapta. | Cada jogador escolhe a própria régua. |
| 2026-11-05 | **Tempo do mundo = tempo real**, com **episódios**: quem está com episódio aberto fica "protegido pelo tempo" (o que acontece depois do seu dia não o atinge) e, ao fechar o episódio, avança para o dia atual do mundo e descobre as consequências (ex.: notícia do meteoro). | Permite jogar em horários diferentes sem um jogador estragar a história aberta do outro. |
| 2026-11-05 | **Ações de grande impacto:** sem bloqueio rígido, mas exigem muita justificativa e têm limites. A lore pode resetar ou restaurar o mundo para a história nunca acabar. | O mundo precisa sobreviver às ações dos jogadores. |
| 2026-11-05 | Novo épico **"Estrutura narrativa"** (AT-12): voz, tom, tamanho das histórias (episódios) e adaptação aos limites de conteúdo. "IA mestra" (AT-5) fica só com o funcionamento por dentro (contexto, rolagens, gravação no mundo). | Separar o que se narra de como a mestra funciona. |
| 2026-11-05 | Projeto do Jira renomeado pelo Osmar de `AHSP` (ArkhamSP) para **`AT` (Arkham Test)**. Chaves `AHSP-N` = `AT-N`. Um projeto Kanban novo pode substituí-lo depois. | O espaço original foi criado no modelo errado. |
| 2026-11-05 | **Personagem de quem está fora (episódio aberto) existe e coexiste:** fica na sua região e rotina, pode conversar, trocar informação e compartilhar coisas pequenas com o outro jogador, mas recusa sair da região ou entrar em perigo; se o outro insistir, arruma uma desculpa e volta à rotina. Sistema de amigos e conhecidos fica para depois. | Quem volta encontra o personagem onde deixou, sem surpresas. |
| 2026-11-04 | Padrões de UI/UX ficam em `docs/padroes-ui.md`, cada um com uma label `ui-<nome>` no Jira. Únicas labels permitidas: `ui-*` e `bug`. | A mesma ideia sempre com a mesma cara, e todos os usos de um padrão fáceis de encontrar para refatorar. |
