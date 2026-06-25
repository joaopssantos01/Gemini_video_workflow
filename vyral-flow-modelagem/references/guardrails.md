# Guardrails (regra inegociável da skill)

1. **Upload de vídeo com pessoa real é livre na etapa de Análise VYRAL (Fase 1).** Não há
   bloqueio aqui — é só leitura, transcrição e modelagem. O usuário pode enviar quantos vídeos de
   referência quiser, mesmo com pessoa identificável.

2. **Nenhum vídeo com pessoa real pode ser usado como referência na geração do clipe no Flow**
   (Fase 4/5). A fronteira do guardrail é o **uso**, não o upload: vídeo com pessoa nunca é
   anexado como `video reference`/`Ingredient de vídeo` na geração — ele serve só de insumo de
   leitura dentro desta skill.

3. **Referências de vídeo permitidas como anexo de geração no Flow:** mão isolada (sem
   rosto/corpo visível), objeto, ilustração/cartoon, ou cena sem qualquer pessoa.

4. **Referência de personagem para geração é sempre imagem**, nunca vídeo de uma pessoa real —
   banco padrão (`assets/personagem-carla/`), foto enviada pelo usuário, ou imagem gerada nesta
   sessão (Nano Banana 2).

5. **Todo item da fila de prontos carrega um aviso de conformidade** antes de ir para o Flow:
   "Confirmação: nenhum vídeo com pessoa real está incluído como referência de geração neste
   clipe."

6. **Se o usuário tentar anexar um vídeo com pessoa numa etapa de geração** (não de análise), a
   skill explica o motivo e oferece a alternativa correta (tratar como insumo de análise, ou
   usar mão/cartoon se o gesto for o que importa) — sem excepcionar mesmo sob pedido explícito.

7. **Sem ambiente descrito no prompt.** O cenário sempre vem da imagem de referência da
   personagem anexada — nunca é escrito em texto no prompt do vídeo.
