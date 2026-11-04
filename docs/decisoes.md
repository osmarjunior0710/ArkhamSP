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
