# Gemini_video_workflow

Skill **VYRAL → Flow** para modelar vídeos de UGC de referência (com pessoa, livres para análise)
e gerar prompts prontos para uso manual no **Google Flow** (Gemini Omni Flash / Veo 3.1).

## O que esta skill faz

1. **Pesquisa profunda do produto** — dossiê + menu de ângulos/públicos/benefícios.
2. **Análise VYRAL** do(s) vídeo(s) de referência — Contexto, Gancho, Problema, Solução, CTA.
3. **Briefing** — quantidade de vídeos/variações, duração, gesto crítico, foto da personagem.
4. **Geração de prompts de vídeo** (principal + variações), com ritmo de fala, tom e gestos
   definidos explicitamente.
5. **Geração de prompts de imagem de referência**, pareados a cada vídeo.

## Regra central

Vídeos com pessoa real podem ser enviados **livremente para análise** (passo 2). Eles **nunca**
são usados como referência na geração do clipe no Flow — ali só entram imagem da personagem,
imagem do produto e, se necessário, vídeo sem pessoa (mão isolada, objeto, cartoon).

## Como instalar

Baixe a pasta `vyral-flow-modelagem/` (ou clone o repositório) e instale como skill no seu
ambiente Gemini/Claude habitual, apontando para `vyral-flow-modelagem/SKILL.md`.

## Estrutura

```
vyral-flow-modelagem/
├── SKILL.md                          — orquestrador principal
├── references/
│   ├── pesquisa-produto.md
│   ├── analise-vyral.md
│   ├── briefing.md
│   ├── personagem-carla-manifesto.md
│   ├── prompt-flow-vyral.md
│   ├── imagens-de-referencia.md
│   └── guardrails.md
└── assets/
    └── personagem-carla/             — banco de fotos de referência da personagem
```

## Banco de fotos da personagem

4 fotos da personagem "Carla" em ambientes/looks diferentes (quarto, corredor, banheiro x2),
cada uma com contexto descrito em `references/personagem-carla-manifesto.md` para a skill
escolher automaticamente qual usar em cada vídeo/variação gerado.
