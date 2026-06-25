# Geração de prompt — vídeo principal e variações (Google Flow / Gemini Omni Flash)

## 0. Fontes que alimentam o prompt

Antes de escrever, combine:
1. **Insight VYRAL** (Fase 1) — estrutura de blocos, gancho, tom.
2. **Briefing** (Fase 2) — produto, tripla ângulo/público/benefício, duração, gesto crítico, foto
   da personagem escolhida.
3. **Pesquisa de produto** (Fase 0, se rodada) — vocabulário e dores reais do comprador.

## 1. Esqueleto do prompt (ordem fixa)

O Gemini Omni Flash, como o antigo Gemini Omni, responde melhor à ordem:
**Subject → Context → Action → Style → Camera → Ambiance → Audio → Technical**

```
SUBJECT: <identity recipe da personagem, EXATA — ver personagem-carla-manifesto.md>

CONTEXT: <referência à imagem anexada como a própria pessoa em selfie — NÃO descreva o
ambiente; ele já vem da foto de referência anexada>

ACTION: <roteiro do bloco, formato fala+gesto pareados — ver Seção 2>

STYLE: <ritmo de fala e tom — ver Seção 3>

CAMERA: <enquadramento explícito — ver Seção 4>

AMBIANCE: <emoção — ver Seção 5>

AUDIO: <fala em PT-BR — ver Seção 6>

TECHNICAL: <bloco de realismo anti-CGI + supressão de herança — ver Seção 7>
```

## 2. Ação + fala (pareadas, frase a frase)

Nunca escreva a fala como bloco solto. Separe cada frase do roteiro da ação física
correspondente, numerado:

```
1. "<fala 1>" — <ação física: pega o produto, olha pra câmera, etc.>
2. "<fala 2>" — <ação física correspondente>
3. "<fala 3 / CTA>" — <ação física, ex.: mostra o rótulo de frente pra câmera>
```

Se houver **gesto crítico** (aplicar produto na mão/rosto) com referência de vídeo de mão/cartoon
anexada: `<ação> segue o ritmo e gesto de mão da referência anexada, mesmo timing`. Sem
referência: descreva lateralidade e direção explicitamente — ex. "aplica com a mão direita na
bochecha esquerda, movimento circular suave, de baixo para cima".

## 3. Ritmo de fala e tom (obrigatório em todo prompt)

Defina sempre os três eixos:
- **Ritmo:** rápido e animado / natural e pausado / lento e confessional — escolha conforme o
  gancho do Insight VYRAL (gancho de afirmação chocante pede ritmo rápido; depoimento íntimo pede
  ritmo mais pausado).
- **Tom:** "amiga conselheira", não "vendedora". Frases curtas, conversacionais. Evite estrutura
  de comercial ("compre já", "não perca"); prefira "eu uso", "eu testei", "vou te mostrar".
- **Gestos:** sempre descreva ao menos 1 gesto de mão livre por bloco (apontar, levantar
  sobrancelha, gesticular animadamente) além do gesto de produto, para fugir de cara estática.

## 4. Câmera e enquadramento (sempre explícito em texto)

Como o vídeo de referência com pessoa não entra na geração, a câmera precisa estar 100% descrita
— não depende de herança:
- **Distância:** selfie / meio-corpo / close-up
- **Ângulo:** altura do rosto, levemente de baixo para cima (selfie de braço estendido)
- **Movimento:** estática (apoiada) ou leve tremor natural de mão, como filmado num iPhone

## 5. Emoção (sempre alta e explícita)

O modelo tende ao neutro — marque sempre: sorriso genuíno, sobrancelhas vivas, movimento de
cabeça animado, energia alta e calorosa, como "compartilhando uma descoberta com a melhor amiga".

## 6. Fala em PT-BR

```
Spoken (Brazilian Portuguese, natural, <ritmo definido na Seção 3>): "<fala completa do bloco>"
```

Reescreva a fala do Insight VYRAL com o produto/contexto do usuário — não copie literalmente o
placeholder, ajuste ao tom natural do roteiro novo.

## 7. Bloco técnico — realismo e supressão (sempre incluir)

```
Realism: real smartphone front-camera selfie, slightly grainy iPhone look, natural skin texture
with visible pores, no beauty filter, photorealistic, NOT CGI, NOT a 3D render.

Suppression: no on-screen text, no captions, no overlay text; product label not mirrored, brand
text readable left-to-right; only one person in frame (the character described); no additional
people in background.
```

## 8. Regras de ouro (não negociáveis)

1. **Nunca descreva o ambiente.** O cenário vem da foto de referência da personagem anexada no
   Flow (ver `personagem-carla-manifesto.md`). Não escreva "in a bathroom", "in a bedroom" etc.
2. **Identidade sempre pela mesma frase exata** (identity recipe) — não reescreva com sinônimos
   de um clipe para o outro na mesma sessão/produto.
3. **Produto sempre com instrução de rótulo legível e não espelhado.**
4. **Nenhum vídeo com pessoa real é anexado como referência de geração** — ver `guardrails.md`.
   Só imagem (personagem/produto) e, se necessário, vídeo sem pessoa (mão/cartoon/objeto).
5. **Cada prompt de vídeo gera também o(s) prompt(s) de imagem de referência correspondente**
   (ver `imagens-de-referencia.md`) — não entregue um prompt de vídeo sem indicar qual imagem vai
   junto.

## 9. Exemplo completo

```
SUBJECT: Carla, mulher branca, cabelo ondulado ruivo-acobreado longo, pele clara com sardas no
rosto, olhos verde-acinzentados, colar fino dourado com pingente de cruz.

CONTEXT: A selfie video of the woman from the reference image, filming herself holding her phone
at arm's length (that's where the camera is).

ACTION:
1. "Gente, vocês não fazem ideia do que eu descobri" — segura o produto perto do rosto, olhando
   pra câmera com expressão animada.
2. "Esse sérum aqui deixou minha pele muito mais uniforme" — vira o produto mostrando o rótulo de
   frente pra câmera, sem espelhar o texto.
3. "Eu uso todos os dias, de manhã e de noite" — aplica o produto com a mão direita na bochecha
   esquerda, movimento circular suave.

STYLE: ritmo rápido e animado, tom de amiga conselheira, gesto de apontar com a mão livre no
bloco 1.

CAMERA: selfie, câmera na altura do rosto, levemente de baixo para cima, leve tremor natural de
mão, como filmado num iPhone.

AMBIANCE: HIGH ENERGY, sorriso genuíno, sobrancelhas vivas, movimento de cabeça animado, como
compartilhando uma descoberta com a melhor amiga.

AUDIO: Spoken (Brazilian Portuguese, natural, fast and excited): "Gente, vocês não fazem ideia do
que eu descobri. Esse sérum aqui deixou minha pele muito mais uniforme. Eu uso todos os dias, de
manhã e de noite."

TECHNICAL: Realism: real smartphone front-camera selfie, slightly grainy iPhone look, natural
skin texture with visible pores, no beauty filter, photorealistic, NOT CGI, NOT a 3D render.
Suppression: no on-screen text, no captions, product label not mirrored, brand text readable
left-to-right, only one person in frame, no additional people in background.
```
