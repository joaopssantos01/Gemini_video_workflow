# Manifesto — Banco de Fotos da Personagem (Carla)

Este arquivo é a fonte que a skill consulta para **escolher a melhor foto de referência** para
cada vídeo/variação, com base no contexto do produto e do roteiro daquele clipe.

> Quando o usuário pedir N vídeos, cada um (ou cada variação) deve usar uma foto **diferente**
> deste banco, escolhida pela combinação ambiente + produto + tom do roteiro. Se o usuário enviar
> fotos próprias além destas, elas entram no mesmo critério de escolha e têm prioridade sobre as
> fotos padrão quando cobrirem melhor o contexto pedido.

## Identity recipe (fixa — usar em todo prompt, palavra por palavra)

```
Carla, mulher branca, cabelo ondulado ruivo-acobreado longo, pele clara com sardas no rosto,
olhos verde-acinzentados, colar fino dourado com pingente de cruz
```

## Fotos disponíveis

### 01 — Quarto rosa, cabelo solto, regata branca
**Arquivo:** `assets/personagem-carla/01_quarto_rosa_cabelo_solto_regata_branca.jpg`
- **Ambiente:** quarto com cabeceira estofada rosa, closet aberto com tênis/bolsas ao fundo,
  pendente de luz redondo de fibra natural, luz quente/ambiente.
- **Cabelo:** solto, ondulado, repartido ao meio.
- **Roupa:** regata canelada branca/off-white.
- **Tom sugerido:** rotina de manhã/quarto, produtos de cuidado pessoal usados em casa,
  conteúdo mais íntimo/morning routine, skincare antes de se vestir, produtos pra cabelo.
- **Combina bem com:** produtos de skincare, cuidados noturnos/matinais, produtos capilares,
  conteúdo "depoimento de quarto".

### 02 — Corredor branco, cabelo preso, camisa branca
**Arquivo:** `assets/personagem-carla/02_corredor_branco_cabelo_preso_camisa_branca.jpg`
- **Ambiente:** corredor/hall minimalista branco, luz embutida no teto, armários claros com
  puxadores metálicos verticais ao fundo.
- **Cabelo:** preso (rabo/meio rabo), rosto mais à mostra.
- **Roupa:** camisa social branca, mangas dobradas.
- **Tom sugerido:** apresentação mais "arrumada", indicada pra produtos com tom mais sério ou
  profissional (ex.: produtos com prova/comparação, depoimento "estou bem", looks de saída).
- **Combina bem com:** produtos de pele com discurso mais técnico/clínico, conteúdo de
  comparação "antes e depois", tom de confiança/autoridade.

### 03 — Banheiro cinza, cabelo solto, regata preta
**Arquivo:** `assets/personagem-carla/03_banheiro_cinza_cabelo_solto_regata_preta.jpg`
- **Ambiente:** banheiro com porcelanato cinza grande-formato, box de vidro, toalha branca
  pendurada — ambiente de banheiro clássico.
- **Cabelo:** solto, ondulado, molhado/recém-lavado (indicado pra produtos pós-banho).
- **Roupa:** regata preta.
- **Tom sugerido:** rotina de skincare pós-banho, produtos pra rosto/corpo aplicados na frente
  do espelho, tom confessional ("acabei de sair do banho e...").
- **Combina bem com:** sérums, hidratantes faciais/corporais, produtos de banho, esfoliantes.

### 04 — Banheiro cinza, cabelo preso, regata cinza
**Arquivo:** `assets/personagem-carla/04_banheiro_cinza_cabelo_preso_regata_cinza.jpg`
- **Ambiente:** mesmo banheiro cinza da foto 03, ângulo mais frontal/próximo.
- **Cabelo:** preso/molhado, rosto totalmente à mostra (boa pra mostrar reação a um produto
  facial de perto).
- **Roupa:** regata cinza mescla.
- **Tom sugerido:** demonstração de produto de perto (aplicar no rosto, mostrar textura),
  formato "passando agora" / close-up de aplicação.
- **Combina bem com:** produtos clareadores, tratamentos faciais, produtos aplicados com a mão
  diretamente no rosto onde o enquadramento precisa estar mais perto.

## Como a skill deve escolher

1. Ler o produto e o tom do roteiro vindos do Briefing (Fase 1).
2. Cruzar com a coluna "Combina bem com" / "Tom sugerido" de cada foto.
3. Se o usuário pedir várias variações/vídeos do mesmo produto, **alternar** entre as fotos que
   combinam — nunca repetir a mesma foto em dois prompts da mesma rodada, a menos que só exista
   uma opção compatível ou o usuário peça explicitamente para manter o mesmo ambiente.
4. Se o usuário enviar fotos próprias da personagem (upload no Briefing), tratá-las com a mesma
   lógica de descrição/contexto e priorizá-las quando cobrirem melhor o pedido.
5. Nunca descrever o ambiente da foto escolhida no prompt do vídeo (ver `prompt-flow-vyral.md`,
   Regra 4) — o ambiente já vem da própria imagem de referência anexada no Flow.
