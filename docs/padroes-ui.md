# Padrões de UI/UX

Catálogo de soluções de interface e funcionalidade já usadas no jogo.
**Objetivo:** a mesma ideia sempre ganha a mesma cara. Se "magias" usam um contador de pips,
"pactos" (ou qualquer recurso contável parecido) usam o mesmo contador.

## Como usar

1. **Antes de criar qualquer tela ou componente**, procurar aqui se já existe um padrão para aquela ideia.
   - Se existe: usar o padrão e colocar a label dele no ticket.
   - Se existe algo parecido, mas não serve exatamente: **perguntar ao Osmar** se é uma variação do padrão
     ou um padrão novo.
   - Se não existe: criar e registrar aqui, como padrão novo.
2. **Cada padrão tem uma label no Jira**: `ui-` + nome curto em kebab-case (ex.: `ui-contador-pips`).
   Todo ticket que cria, usa ou altera o padrão recebe a label.
3. **Para mudar um padrão no futuro**, buscar todos os tickets com
   `project = AHSP AND labels = ui-<nome>` e a seção "Onde é usado" abaixo, e refatorar tudo junto.

## Regras das labels (para não virar bagunça)

- Só existem dois tipos de label no projeto:
  - `ui-<nome>`: um padrão deste arquivo. **Toda label `ui-` precisa estar registrada aqui.**
  - `bug`: marca de subbug (subtask de bug).
- Sem labels de status, prioridade ou épico: o Jira já tem campos para isso.
- Nome em português, minúsculo, sem acento, com hífen (ex.: `ui-barra-de-vida`, não `UI_BarraVida`).
- Criar uma label nova só quando um padrão novo for registrado aqui.

## Modelo de registro

```
### <Nome do padrão>
- **Label:** `ui-<nome>`
- **Ideia:** que problema do jogador resolve
- **Quando usar:** em que situações aplicar (e quando NÃO usar)
- **Como é:** aparência e comportamento (estados, cores, interação)
- **Variações permitidas:** o que pode mudar sem virar outro padrão (ex.: rótulo, cor do tema)
- **Onde é usado:** telas/componentes + tickets (AHSP-N)
- **Histórico:** data — o que mudou e por quê (ticket)
```

---

## Padrões registrados

### Rolagem 2d12 (Bênção e Mythos) — rascunho, em prova de conceito
- **Label:** `ui-rolagem-2d12`
- **Ideia:** o jogador vê os dois dados caírem e entende na hora quem "ganhou", a Bênção ou o Mythos.
- **Quando usar:** todo teste com risco (regra do épico AHSP-6). Não usar para sorteios internos da IA.
- **Como é:**
  - dois d12 3D caem juntos e param com o valor sorteado na face de cima, com o número de pé para o jogador;
  - **branco = Bênção** (número escuro), **preto = Mythos** (número claro); o branco fica à esquerda;
  - 6 e 9 têm um sublinhado;
  - depois que os dados param, um cartão mostra o **tipo de resultado** em destaque e a conta por extenso
    ("Bênção 7 + Mythos 5 + 0 = 12 contra 14");
  - cor do cartão por resultado: Crítico = dourado claro; Sucesso = verde; Sucesso com deslize e Falha com progresso = amarelo; Falha = vermelho.
- **Variações permitidas:** tamanho da área dos dados; o tema de cor da mesa.
- **Onde é usado:** prova de conceito `poc/dados-3d.html` (AHSP-10).
- **Histórico:** 2026-11-05 — criado na prova de conceito (AHSP-10).
