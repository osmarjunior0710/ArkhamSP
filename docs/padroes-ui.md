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
   `project = AT AND labels = ui-<nome>` e a seção "Onde é usado" abaixo, e refatorar tudo junto.

## Regras das labels (para não virar bagunça)

- Só existem dois tipos de label no projeto:
  - `ui-<nome>`: um padrão deste arquivo. **Toda label `ui-` precisa estar registrada aqui.**
  - `bug`: marca de subbug (subtask de bug).
- Sem labels de status, prioridade ou épico: o Jira já tem campos para isso.
- Nome em português, minúsculo, sem acento, com hífen (ex.: `ui-barra-de-vida`, não `UI_BarraVida`).
- Criar uma label nova só quando um padrão novo for registrado aqui.

## Fundamentos (valem para todas as telas)

- **Espaçamento:** escala em passos de 4 px: 1 = 4 px, 2 = 8 px, **3 = 12 px (padrão do projeto)**, 4 = 16 px, 5 = 20 px. Cartões, linhas e grupos usam o nível 3; só sobe com motivo.
- **Botões:** altura mínima 40 px, espaçamento interno 8 × 14 px, texto em Cinzel 0,85rem. Nada de botões gigantes.
- **Celular primeiro:** informação que o jogador precisa consultar o tempo todo (ex.: pontos para distribuir) fica **fixa no topo**; ações principais (Voltar / Continuar) ficam numa **barra fixa embaixo**, com espaço vazio no fim da página para nada ficar escondido.
- **Teste:** celular 390 × 844 e computador 1280 × 800 (ver `CLAUDE.md`).
- Decidido em 2026-11-09 (AT-20, AT-22).

---

## Modelo de registro

```
### <Nome do padrão>
- **Label:** `ui-<nome>`
- **Ideia:** que problema do jogador resolve
- **Quando usar:** em que situações aplicar (e quando NÃO usar)
- **Como é:** aparência e comportamento (estados, cores, interação)
- **Variações permitidas:** o que pode mudar sem virar outro padrão (ex.: rótulo, cor do tema)
- **Onde é usado:** telas/componentes + tickets (AT-N)
- **Histórico:** data — o que mudou e por quê (ticket)
```

---

## Padrões registrados

### Rolagem 2d12 (Bênção e Mythos) — oficial

> **Implementação de referência aprovada pelo Osmar:** `poc/dados-3d.html` (Artifact
> https://claude.ai/artifact/3PLztSz9M4ZdQwF7L9kn3P, versão 2). "É o que eu quero no final."
> Não apagar nem alterar esse arquivo: a versão do jogo deve reproduzir este comportamento.
- **Label:** `ui-rolagem-2d12`
- **Ideia:** o jogador vê os dois dados caírem e entende na hora quem "ganhou", a Bênção ou o Mythos.
- **Quando usar:** todo teste com risco (regra do épico AT-6). Não usar para sorteios internos da IA.
- **Como é:**
  - dois d12 3D são lançados juntos de um lado da mesa, com **física real**: batem nas bordas, esbarram um no
    outro e quicam até parar; a face de cima mostra o valor sorteado, com o número de pé para o jogador;
  - som de batida proporcional à força do impacto, com botão "Som: ligado/desligado";
  - **branco = Bênção** (número escuro), **preto = Mythos** (número claro); a legenda no canto identifica as cores;
  - 6 e 9 têm um sublinhado;
  - depois que os dados param, um cartão mostra o **tipo de resultado** em destaque e a conta por extenso
    ("Bênção 7 + Mythos 5 + 0 = 12 contra 14");
  - cor do cartão por resultado: Crítico = dourado claro; Sucesso = verde; Sucesso com deslize e Falha com progresso = amarelo; Falha = vermelho.
- **Variações permitidas:** tamanho da área dos dados; o tema de cor da mesa.
- **No jogo (decisão de 2026-11-07):** o dado branco se chama **Esperança** (a prova de conceito ainda mostra "Bênção"). Com vantagem ou desvantagem entram **3 dados** (2 Esperança + 1 Mythos, ou o contrário do lado dos inimigos): como mostrar o dado descartado ainda será desenhado.
- **Onde é usado:** prova de conceito `poc/dados-3d.html` (AT-10).
- **Histórico:**
  - 2026-11-05: criado na prova de conceito (AT-10), com animação roteirizada.
  - 2026-11-05: física real e som de batida (AT-11), após o Osmar achar a v1 "roteirizada, sem punch".
  - 2026-11-05: aprovado pelo Osmar como padrão oficial e visual final dos dados.

### Barra de Sanidade — rascunho
- **Label:** `ui-barra-sanidade`
- **Ideia:** o jogador bate o olho e sabe em que estado mental o personagem está, sem fazer conta.
- **Quando usar:** sempre que a Sanidade do personagem aparecer (ficha, tela de jogo).
- **Como é:**
  - barra de 12 pontos dividida em **4 blocos de 3**, esvaziando da direita para a esquerda conforme a Sanidade cai;
  - ao lado, o **nome do estado** do bloco atual: **Lúcido** (12–10), **Abalado** (9–7), **Perturbado** (6–4), **Fraturado** (3–1), **Insano** (0);
  - o número atual aparece junto (ex.: "Abalado · 8").
  - **cores (decisão do Osmar, 2026-11-09):** por enquanto a barra é sempre **verde** (casas atuais) e **verde escuro** (casas perdidas), em qualquer estado; o estado aparece só no nome. Usar a cor do estado na barra ficou estranho e será repensado.
- **Variações permitidas:** a definir quando a primeira tela for construída.
- **Onde é usado:** jogo (`jogo/arkhamsp.html`): passo "Corpo e mente" da criação e resumo do personagem (AT-17, AT-16).
- **Histórico:** 2026-11-08: nomes dos estados definidos pelo Osmar; primeira tela que usa: AT-17. 2026-11-09: casas perdidas em cor escura (AT-26); barra fixada em verde / verde escuro (AT-26).

### Pips de pontos — rascunho
- **Label:** `ui-pips`
- **Ideia:** distribuir ou mostrar valores pequenos (0 a 3, 0 a 5) de forma visual, contando "bolinhas".
- **Quando usar:** atributos, especializações e qualquer recurso contável pequeno (ex.: o que antes seriam "magias" e "pactos" usam este mesmo padrão). Não usar para valores grandes (Vida/Lucidez usam barra de células; Sanidade usa `ui-barra-sanidade`).
- **Como é:**
  - linha com nome e descrição curta à esquerda (no celular, as bolinhas vão para baixo do nome); à direita, na ordem: **bolinhas, botão −, número, botão +**;
  - **sempre mostra o máximo do jogo (5 bolinhas)**: cheias = latão (ponto usado); contorno latão = disponível; **contorno tracejado cinza = bloqueado** (libera ao evoluir); uma legenda curta explica os três estados;
  - clicar numa bolinha define o valor até ela; clicar na última cheia diminui 1;
  - quando há um orçamento (ex.: 8 pontos), o contador "N pontos para distribuir" fica **na barra fixa do topo**; verde quando zera; + e bolinhas que estourariam o orçamento ficam desabilitados.
- **Variações permitidas:** número máximo de bolinhas; **somente leitura** (bolinhas menores, sem − e +, sem número; vazias em cinza): usada na prévia/ficha do personagem.
- **Onde é usado:** criação de personagem, passos Atributos e Perícias (AT-17).
- **Histórico:** 2026-11-08: criado em AT-17. 2026-11-09: 5 bolinhas sempre visíveis com bloqueadas em cinza; contador na barra fixa (AT-20, AT-21). 2026-11-09: ordem "bolinhas − número +"; versão somente leitura na prévia (AT-25).

### Cartões de escolha — rascunho
- **Label:** `ui-cartao-escolha`
- **Ideia:** escolher uma entre poucas opções que precisam de explicação.
- **Quando usar:** 2 a 4 opções com título e descrição (ex.: modo de mortalidade). Para opções curtas sem explicação, usar a régua segmentada (Leve / Moderado / Pesado).
- **Como é:** cartões lado a lado (empilham no celular), título em Cinzel e descrição curta; o escolhido ganha borda latão e um ✓.
- **Variação "cartão de navegação":** cartão em largura total que, ao tocar, já leva para a próxima tela (sem ✓). Pode ter uma etiqueta latão no topo (ex.: "EM BREVE"). Desabilitado fica com opacidade baixa e o texto explica por quê.
- **Onde é usado:** criação de personagem, passo "Tipo de história" (AT-17); escolha do modo de criação, como cartão de navegação (AT-19).
- **Histórico:** 2026-11-08: criado em AT-17. 2026-11-10: variação "cartão de navegação" (AT-19).

### Assistente em passos — rascunho
- **Label:** `ui-assistente-passos`
- **Ideia:** dividir um processo longo (criar personagem) em passos curtos, sem perder a noção de onde se está.
- **Como é:**
  - **barra fixa no topo:** "Passo N de 6 · Nome do passo", barra de progresso em 6 segmentos (atual em latão) e, quando o passo tem pontos, o contador à direita;
  - conteúdo do passo;
  - **barra fixa embaixo:** "Voltar" (ou "Cancelar" no primeiro) à esquerda e "Continuar" (ou a ação final, ex.: "Criar personagem") à direita; a mensagem de erro aparece dentro dessa barra, acima dos botões, para nunca ficar fora da tela;
  - ao tentar avançar com algo faltando, a mensagem diz o que falta; nada avança sozinho.
- **Onde é usado:** criação de personagem (AT-17).
- **Histórico:** 2026-11-08: criado em AT-17. 2026-11-09: pílulas trocadas por barra fixa compacta no topo; botões em barra fixa embaixo (AT-20).

### Régua com exemplo — rascunho
- **Label:** `ui-regua-exemplo`
- **Ideia:** escolher um nível (ex.: Leve / Moderado / Pesado) vendo na hora o que ele significa.
- **Quando usar:** escolhas de intensidade em que o nome do nível sozinho não explica (limites de conteúdo).
- **Como é:** nome à esquerda e régua segmentada em pílula à direita (opção atual em latão); embaixo, um **exemplo de narração** em fonte de história, com barra latão à esquerda, que muda ao trocar o nível.
- **Onde é usado:** criação de personagem, passo "Tipo de história" (AT-23).
- **Histórico:** 2026-11-09: criado em AT-23.

### Confirmar ação destrutiva — rascunho
- **Label:** `ui-confirmar-acao`
- **Ideia:** impedir que o jogador perca algo sem querer (ex.: apagar personagem).
- **Quando usar:** qualquer ação que não dá para desfazer.
- **Como é:** o botão da ação tem contorno vermelho ("Apagar"). Ao tocar, abre **dentro do próprio item** uma confirmação: frase em vermelho dizendo o que vai acontecer e que não dá para desfazer ("Apagar Victor para sempre? Não dá para desfazer."), com "Cancelar" e "Apagar para sempre". Nada de janelas do navegador.
- **Onde é usado:** Lista de personagens (AT-24).
- **Histórico:** 2026-11-09: criado em AT-24.

### Barra de recurso (Vida, Lucidez) — rascunho
- **Label:** `ui-barra-recurso`
- **Ideia:** ver de relance quanto o personagem tem, quanto já perdeu e qual é o máximo dele, pronto para dano e cura.
- **Quando usar:** Vida e Lucidez (e qualquer recurso futuro que tenha atual e máximo).
- **Como é:**
  - 9 casas (o máximo possível no jogo), em linha, com o nome à esquerda e o número à direita;
  - **atual:** cor cheia (Vida = vermelho, Lucidez = azul);
  - **perdido** (entre o atual e o máximo do personagem): a mesma cor, **escura**;
  - **indisponível** (acima do máximo do personagem): **contorno tracejado cinza**, como as bolinhas bloqueadas de `ui-pips`;
  - o número mostra "atual/máximo" quando o personagem está machucado (ex.: "6/7"), e só o valor quando está cheio.
- **Exemplo:** Vida máxima 7, tomou 1 de dano → 6 vermelhas, 1 vermelha escura, 2 tracejadas.
- **Onde é usado:** criação (passo Corpo e mente) e prévia do personagem (AT-26).
- **Histórico:** 2026-11-09: criado em AT-26, a pedido do Osmar, para preparar a futura calculadora de dano.
