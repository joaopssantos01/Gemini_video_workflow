# Imagens de referência — pareadas a cada prompt de vídeo

Depois da fila de prompts de vídeo estar pronta (Fase 4), gere também o(s) prompt(s) de imagem
de referência que vão junto de cada vídeo.

## 1. O que cada vídeo/variação precisa em imagens

- **Imagem da personagem** — sempre obrigatória. Vem do banco padrão
  (`assets/personagem-carla/`), de foto enviada pelo usuário, ou gerada nesta sessão (ver
  `briefing.md`, Seção 3). Reaproveite a mesma imagem entre vídeos quando o contexto pedir o
  mesmo ambiente/tom; varie quando o briefing pedir diversidade entre variações.
- **Imagem do produto** — sempre obrigatória, enviada pelo usuário.
- **Imagem de cena/gesto adicional** — só se o briefing indicar necessidade (ex.: closeup de uma
  textura específica do produto) e não houver vídeo de mão/cartoon disponível para aquele gesto.

## 2. Reaproveitamento vs. geração nova

Por padrão, **reaproveite** imagens já existentes (banco padrão + uploads do usuário) sempre que
cobrirem o contexto pedido. Só proponha gerar uma imagem nova quando:
- Nenhuma foto do banco/enviada combina com o ambiente/tom pedido pelo briefing, ou
- O usuário pediu explicitamente uma variação de cena nova.

Quando gerar: usar Nano Banana 2 no próprio chat do Gemini, mantendo a identity recipe da
personagem (ver `personagem-carla-manifesto.md`) e descrevendo só o que muda (ambiente, roupa,
penteado, pose) — sem alterar os traços fixos de identidade.

## 3. Como entregar na fila de prontos

Para cada item da fila (Fase 5), liste explicitamente:
```
Vídeo/variação N — produto: <nome>
  Prompt de vídeo: <ver prompt-flow-vyral.md>
  Imagem personagem: <caminho/URL — banco padrão | enviada pelo usuário | gerada nesta sessão>
  Imagem produto: <URL enviada pelo usuário>
  [Imagem/vídeo de gesto, se aplicável]: <caminho/URL>
```

Isso garante que, na hora de executar manualmente no Flow, o usuário sabe exatamente quais
arquivos anexar junto com aquele prompt específico.
