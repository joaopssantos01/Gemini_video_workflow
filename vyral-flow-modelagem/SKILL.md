---
name: vyral-flow-modelagem
description: Analisa vídeo(s) de referência de UGC (com pessoa, sem restrição de upload) no formato Insight VYRAL (Contexto/Gancho/Problema/Solução/CTA), faz pesquisa profunda do produto, conduz o briefing e gera os prompts de vídeo (principal + variações) e de imagem de referência para gerar manualmente no Google Flow (Gemini Omni Flash / Veo). Use SEMPRE que o usuário enviar um vídeo de referência do TikTok/Instagram pedindo para "modelar", "analisar", "fazer um igual", "recriar esse vídeo", "fazer uma análise VYRAL", ou pedir para gerar N vídeos/variações de UGC com a personagem a partir de um ou mais vídeos de inspiração. A skill NUNCA usa vídeo com pessoa real como referência de geração no Flow — só como insumo de análise; a geração usa apenas imagem da personagem (banco em assets/personagem-carla/), imagem do produto, e (se necessário) vídeo sem pessoa (mão/objeto/cartoon). Cada vídeo/variação pedido usa uma foto diferente da personagem, escolhida pelo contexto. NÃO usar para disparar a geração em si (isso é manual, feito pelo usuário direto no Flow) nem para dublagem/legenda/agendamento (etapas de outro pipeline).
---

# VYRAL → Flow: Análise, Briefing e Geração de Prompts para UGC

Pipeline para modelar vídeos de UGC de referência (com pessoa, livre para análise) e produzir os
prompts prontos para gerar manualmente no Google Flow (Gemini Omni Flash / Veo 3.1) — sem nunca
usar vídeo com pessoa real como referência de geração.

## Quando usar

- Usuário envia 1+ vídeos de referência (TikTok/Instagram, com pessoa) e pede para modelar,
  analisar, recriar, ou gerar N vídeos/variações inspirados neles.
- Usuário já tem um produto e quer roteiro + prompt pronto para colar no Flow.
- Usuário pede "análise VYRAL" de um vídeo.

## Como NÃO usar

- Não dispara nada automaticamente no Flow — a geração é manual, feita pelo usuário.
- Não faz dublagem, legenda ou agendamento (pipelines separados, fora do escopo desta skill).
- Não cria corte físico de arquivo de vídeo — os blocos identificados na análise são só
  estrutura de roteiro, nunca clipes recortados para upload.

## Fluxo (5 fases, em ordem)

### Fase 0 — Pesquisa profunda do produto
Ler `references/pesquisa-produto.md`. Usuário sempre envia a imagem do produto. Pesquisa nativa
(web) → mini-dossiê (descrição, público, motivos de compra, dores ocultas, qualidades
destacadas) → menu de ângulos/públicos/benefícios para o usuário escolher.

### Fase 1 — Análise VYRAL do(s) vídeo(s) de referência
Ler `references/analise-vyral.md`. Vídeo(s) com pessoa real entram livremente aqui — são insumo
de leitura/transcrição, nunca de geração (ver `references/guardrails.md`). Gerar o Insight VYRAL
(Contexto/Gancho/Problema/Solução/CTA + "copie o que funcionou") por vídeo ou consolidado.

### Fase 2 — Briefing
Ler `references/briefing.md`. Perguntar: quantidade de vídeos/variações, tripla
ângulo/público/benefício por vídeo, duração-alvo (até 10s por clipe — teto seguro de upload no
Flow hoje), gesto crítico (e se há referência de mão/cartoon), e foto da personagem (banco
padrão, enviada pelo usuário, ou gerada nesta sessão).

Escolha de foto da personagem: ler `references/personagem-carla-manifesto.md`. Por padrão a
skill escolhe pelo contexto, sem precisar perguntar. **Cada vídeo/variação pedido deve usar uma
foto diferente** do banco — nunca repetir a mesma foto em dois prompts da mesma rodada, a menos
que só exista uma opção compatível ou o usuário peça para manter o mesmo ambiente.

### Fase 3 — Geração dos prompts de vídeo (principal + variações)
Ler `references/prompt-flow-vyral.md`. Estrutura fixa Subject → Context → Action → Style →
Camera → Ambiance → Audio → Technical. O prompt define explicitamente: ritmo da fala, tom, e
gestos (ver Seção 3 daquele arquivo) — nunca descreve o ambiente (vem da foto de referência
anexada).

### Fase 4 — Geração dos prompts de imagem de referência
Ler `references/imagens-de-referencia.md`. Para cada prompt de vídeo, parear o(s) prompt(s) de
imagem (personagem + produto + gesto, se aplicável), priorizando reaproveitar imagens já
existentes.

### Saída final
Para cada vídeo/variação, entregar em sequência:
```
Vídeo/variação N — produto: <nome>, ângulo: <ângulo escolhido>

[Prompt de vídeo completo]

Imagem personagem: <caminho/URL>
Imagem produto: <URL enviada pelo usuário>
[Imagem/vídeo de gesto, se houver]: <caminho/URL>
```
O usuário cola o prompt e sobe as referências manualmente no Flow.

## Guardrails (ler sempre)

Ler `references/guardrails.md` antes de montar qualquer prompt de geração. Resumo: vídeo com
pessoa real é livre para a Fase 1 (análise), mas nunca entra como referência nas Fases 3/4
(geração) — ali só imagem de personagem/produto e, se necessário, vídeo sem pessoa.

## Estrutura de arquivos da skill

```
vyral-flow-modelagem/
├── SKILL.md
├── references/
│   ├── pesquisa-produto.md          (Fase 0)
│   ├── analise-vyral.md             (Fase 1)
│   ├── briefing.md                  (Fase 2)
│   ├── personagem-carla-manifesto.md (banco de fotos + lógica de escolha)
│   ├── prompt-flow-vyral.md         (Fase 3)
│   ├── imagens-de-referencia.md     (Fase 4)
│   └── guardrails.md                (regra inegociável, ler sempre)
└── assets/
    └── personagem-carla/
        ├── 01_quarto_rosa_cabelo_solto_regata_branca.jpg
        ├── 02_corredor_branco_cabelo_preso_camisa_branca.jpg
        ├── 03_banheiro_cinza_cabelo_solto_regata_preta.jpg
        └── 04_banheiro_cinza_cabelo_preso_regata_cinza.jpg
```
