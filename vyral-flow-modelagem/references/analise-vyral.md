# Análise VYRAL — como modelar o vídeo de referência

Vídeos com pessoa real **podem ser enviados livremente** para esta etapa — aqui é só leitura e
modelagem, nunca entram como referência de geração (ver `guardrails.md`).

## 1. Receber e ler o vídeo

Para cada vídeo de referência enviado:
- **Transcrever a fala** integralmente (fonte da verdade para recriar a narração depois).
- **Ler a cena**: enquadramento (selfie de braço? plano fixo? em pé/sentado?), cenário, produto
  mostrado, texto on-screen (headline, preço, setas), gestos, ritmo de corte.
- **Identificar os blocos de fala** — trechos de fala contínua separados por pausas naturais.
  Isso não gera corte físico de arquivo (o vídeo nunca vai para o Flow); serve só para estruturar
  o roteiro novo em blocos equivalentes.

Se houver 2+ vídeos de referência, consolide o padrão comum (estrutura de fala, tipo de gancho,
enquadramento) antes de gerar o Insight final.

## 2. Gerar o Insight VYRAL

Sempre no mesmo formato — Contexto, Gancho, Problema, Solução, CTA, e o bloco "Copie o que
funcionou":

```
💡 Insight VYRAL

🧩 Contexto:
<o que o vídeo é, de forma resumida — formato de conteúdo, tipo de demonstração>

🪝 Gancho:
<a abertura que prende atenção — tipo de gancho (afirmação chocante, chamada direta, pergunta) +
exemplo da frase usada>

💔 Problema:
<a dor evocada — qual sofrimento/frustração o vídeo nomeia>

💡 Solução:
<como o produto resolve e como isso é demonstrado em cena>

🚀 CTA:
<como o vídeo fecha o convite à ação>

🔥 Copie o que funcionou:
<bloco de texto-modelo da fala, com placeholders entre colchetes substituindo os termos
específicos do vídeo original — ex.: [PRODUTO], [PROBLEMA], [CARACTERÍSTICA], [RESULTADO],
[NOME], [IDADE], [COR] — pronto para reescrever com o produto do usuário>
```

### Exemplo de placeholder (referência de tom)
> "Olha isso. Essa é a única [PRODUTO] que não vai deixar seu [PROBLEMA] depois de [AÇÃO]. E o
> segredo é isso aqui. A [PRODUTO] tem essa tecnologia [CARACTERÍSTICA] que tem justamente essa
> função. (...) Essa [PRODUTO] tá muito viralizada e tem pouquíssimas no estoque."

Mantenha o tom do vídeo original no placeholder (amiga-conselheira, depoimento pessoal, tutorial
direto, etc.) — isso é o que o roteiro novo (Fase 3) vai herdar.

## 3. Saída desta etapa

Um Insight VYRAL por vídeo enviado (ou um Insight consolidado, se 2+ vídeos compartilharem
padrão), pronto para alimentar o Briefing (Fase 2) e a geração de prompts (Fase 4).
