# Briefing

Depois do Insight VYRAL (e da Pesquisa de Produto, se rodada), pergunte ao usuário:

## 1. Perguntas obrigatórias

- **Produto:** confirmar a imagem já enviada (ou pedir, se ainda não veio).
- **Quantidade de vídeos/variações:** quantos vídeos o usuário quer a partir deste Insight.
- **Ângulo/público/benefício:** qual tripla do menu da pesquisa de produto usar em cada
  vídeo/variação (uma tripla por vídeo, se houver mais de um).
- **Duração-alvo:** até 10s por clipe é o teto seguro de upload no Google Flow hoje (vídeos
  acima disso têm causado falha de upload/análise na ferramenta). Para vídeos mais longos,
  trate como múltiplos clipes de até 10s gerados separadamente no Flow.
- **Gesto crítico:** algum bloco do roteiro mostra a mão aplicando o produto (rosto, corpo,
  cabelo)? Se sim, o usuário tem um vídeo de referência de mão isolada/cartoon para anexar à
  geração, ou o gesto deve ser só descrito em texto no prompt?

## 2. Pergunta sobre fotos de referência da personagem

Por padrão, a skill escolhe as fotos do banco padrão (`personagem-carla-manifesto.md`) com base
no contexto do produto/roteiro — sem precisar perguntar nada, a menos que o usuário queira
participar da escolha ou enviar fotos próprias.

Perguntar apenas se for ambíguo ou se o usuário sinalizar interesse:
- O usuário quer enviar fotos próprias da personagem para usar em vez das do banco padrão?
- O usuário quer **gerar** novas fotos/variações de cena para esta rodada (em vez de usar as do
  banco)?

## 3. Geração de imagens de referência (opcional, só se o usuário pedir)

**Padrão da skill: usar somente o conteúdo já existente** — fotos do banco padrão
(`assets/personagem-carla/`) e/ou fotos que o usuário enviar nesta conversa. Não gerar imagem
nova por padrão.

**Se o usuário optar por criar imagens novas:**
- Gerar usando o **Nano Banana 2**, diretamente no chat do Gemini onde esta skill está rodando
  (não chamar API externa — a skill assume que o ambiente de execução já é o Gemini com acesso
  nativo de geração de imagem).
- A nova imagem gerada deve manter a identity recipe da personagem (ver manifesto) e variar
  ambiente/roupa/penteado conforme o pedido do usuário.
- Depois de gerada e aprovada, tratar essa imagem como mais uma opção do banco de fotos para
  aquela rodada (pode ser reaproveitada entre os vídeos da mesma sessão).

## 4. Saída desta etapa

Briefing completo por vídeo/variação: produto + tripla (ângulo/público/benefício) + duração-alvo
+ gesto crítico (sim/não, e referência se houver) + foto da personagem escolhida (banco padrão,
enviada pelo usuário, ou gerada nesta etapa). Segue para a geração de prompts.
