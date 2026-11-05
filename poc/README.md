# Provas de conceito

| Arquivo | O que é | Status |
|---|---|---|
| `dados-3d.html` | Dois d12 3D (branco = Bênção, preto = Mythos) com física real e som. Artifact: https://claude.ai/artifact/3PLztSz9M4ZdQwF7L9kn3P | **Referência aprovada** (AT-10, AT-11). É o visual final dos dados: não apagar nem alterar. |
| `pilar-masp.html` | Teste de mundo compartilhado entre contas: a mestra narra na conta de quem joga e as inscrições no pilar do MASP ficam num banco comum. Artifact: https://claude.ai/artifact/1a7rA8U3SfqXk5uivaTYaM | Em teste (AT-13). Descartável. |

## Como os dados funcionam (resumo para reaproveitar no jogo)

1. O resultado é sorteado **antes** (`crypto.getRandomValues`).
2. A física (cannon.js 0.6.2) é simulada inteira sem desenhar, até os dois dados pararem; se algum parar inclinado, simula de novo.
3. Vê-se qual face ficou para cima e os números das faces são trocados para que ela mostre o valor sorteado (faces opostas continuam somando 13).
4. O número da face de cima é desenhado de pé para a câmera.
5. A simulação gravada é reproduzida a 60 quadros por segundo, tocando um estalo a cada batida.

Detalhes técnicos completos (parâmetros de física, materiais, som) nos comentários de AT-10 e AT-11 no Jira.
