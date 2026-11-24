# Formatos de arquivo

Estado 2026-11-24 · listas `pt-2026-11-20+sha256:f65d68400f3a`

Todos os arquivos estão em UTF-8, na forma normal NFC, com quebras de linha LF. Os TSV têm uma linha de
cabeçalho e separam as colunas com uma tabulação; não há aspas nem escapes. Os decimais usam ponto.

**Formas** (`form`, `lemma`, `w`, `leit`, `bonus`) se escrevem em minúsculas e **com as letras das
peças**: só a–z. As letras perdem acentos, til e cedilha (*coração* → `coracao`, *ônibus* → `onibus`).
A grafia real, com acentos, está em `show` / `bonusShow`. Uma forma das listas tem de 3 a 10 letras
(as de solução, de 3 a 8); uma forma básica (`lemma`) pode ser mais curta ou mais longa. Ordem: pelas
letras, de a a z.

Os nomes de arquivo e de coluna vêm do repositório alemão (`ziel` = objetivo, `entscheidung` = decisão,
`grund` = motivo), para que as mesmas ferramentas leiam os dois.

## data/ziel.tsv — vocabulário de solução

As palavras que um passatempo pode pedir. Uma linha por **leitura**: uma forma que pertence a várias
formas básicas aparece várias vezes. A primeira linha de uma forma é a leitura que o gerador trata como
principal (forma básica e classe). As linhas estão ordenadas por `form` e, dentro de uma forma, nessa
ordem.

| Coluna | Conteúdo | Exemplo |
| --- | --- | --- |
| `form` | a forma, com as letras das peças | `comeu` |
| `show` | grafia real, em minúsculas, com acentos; igual em todas as linhas de uma forma | `comeu` |
| `lemma` | forma básica desta leitura, com as letras das peças | `comer` |
| `pos` | classe: `noun` substantivo, `verb` verbo, `adj` adjetivo, `adv` advérbio, `pron` pronome, `prep` preposição, `conj` conjunção, `num` numeral, `other` artigos e outras | `verb` |
| `zipf` | frequência da forma na escala Zipf, duas casas decimais: log10 da soma das frequências de todas as suas grafias aceitas (*esta* + *está*); igual em todas as linhas de uma forma | `4.38` |

- **Zipf** é o logaritmo decimal das ocorrências por bilhão de palavras: 3 é uma vez por milhão, 6 uma
  vez por mil. Os valores vêm do wordfreq (veja SOURCES.md). Algumas palavras estão abaixo do limiar e
  são de solução porque uma lista manual as acrescenta (`curation/always-target.txt`).
- Cada palavra de solução é comum **no Brasil e em Portugal**: além do limiar, ela passa pela prova de
  variedade (suas frequências nas legendas brasileiras e portuguesas do FrequencyWords não diferem demais
  (com suavização: (máx + 1) / (mín + 1) por milhão abaixo de 8; os gerúndios seguem a prova do seu verbo, porque *fazendo* é a mesma palavra nos dois países, e *você* é palavra de solução por decisão à mão)) e não tem só sentidos marcados como de um país. Formas verbais de *vós*,
  mais-que-perfeitos simples raros e palavras estrangeiras com k, w ou y nunca são de solução.
- Quando a forma perde uma cedilha ou um til e então se lê como outra palavra corrente (*força* →
  FORCA, *amanhã* → AMANHA), ela não é de solução; isso vale também quando a outra palavra é uma forma
  flexionada (*amanha*, de *amanhar*). As exceções revistas uma a uma estão em `curation/fold-ok.txt`.
- Um passatempo pede no máximo uma forma por forma básica.

9,011 formas em 12,837 linhas; as primeiras leituras pertencem a 5,867
formas básicas.

## data/bonus.tsv — palavras aceitas

Cada forma que o jogo aceita, com sua grafia. Todas as formas de `ziel.tsv` estão aqui também. Ordenado
por `form`.

| Coluna | Conteúdo | Exemplo |
| --- | --- | --- |
| `form` | a forma | `coracao` |
| `show` | grafia real, em minúsculas, com acentos | `coração` |

```
coracao	coração
esta	está
facto	facto
fato	fato
onibus	ônibus
```

- Uma linha por forma. Valem as duas grafias atuais do Acordo Ortográfico de 1990 (*fato* e *facto*,
  *contato* e *contacto*), cada uma como forma própria; as grafias anteriores a 1990 (*acção*, *óptimo*)
  não estão na lista.
- Cada forma tem uma grafia de exibição: primeiro a lista manual (`curation/spelling-priority.txt`),
  depois uma grafia que não seja só forma de *vós* ou mais-que-perfeito, depois a brasileira quando as
  duas normas diferem só no acento (*econômico*, não *económico*), depois a mais frequente nas legendas
  brasileiras e no wordfreq.
- Dias da semana, meses e nomes de línguas se escrevem em minúsculas.

312,253 formas.

## data/levels.json, data/daily.json — passatempos

Os dois arquivos têm o mesmo formato: um objeto JSON, uma página por linha.

| Campo | Conteúdo |
| --- | --- |
| `v` | versão do formato, agora `1` |
| `lang` | idioma do livro, `pt` (o livro alemão não tem esse campo) |
| `lexicon` | estado das listas com que os passatempos foram gerados e verificados (o mesmo que `lexicon` em `VERSION`): `pt-`, a data das fontes e parte de uma soma de verificação das listas; não pode ser recalculado a partir deste repositório porque inclui a lista de filtro não publicada |
| `generator` | programa e versão que geraram os passatempos |
| `pages` | as páginas |

### Uma página

| Campo | Conteúdo |
| --- | --- |
| `page` | número da página, 1–640 no livro; nos passatempos do dia, o número sequencial |
| `bogen` | capítulo 1–40, de 16 páginas; `0` nos passatempos do dia |
| `kind` | `kreuz` (palavras cruzadas) ou `freisatz` (o pico: palavras sem cruzamentos, lidas da esquerda para a direita, linha por linha) |
| `theme` | só no livro, a partir do capítulo 3: o tema do capítulo como identificador interno, p. ex. `garten` (os identificadores são alemães; o app mostra um nome em português) |
| `leit` | palavra-chave: a palavra de solução que usa todas as peças |
| `tiles` | as peças da roda na posição inicial, no sentido horário a partir do topo: maiúsculas `A`–`Z`, sem acentos, til nem cedilha. O livro em português não tem peças duplas |
| `cols`, `rows` | só em `kreuz`: largura e altura da grade em casas, no máximo 10 × 8 |
| `words` | as palavras de solução, veja abaixo |
| `bonus` | as palavras extras: cada forma da lista aceita que se pode formar com as peças e não é de solução na página; completa e ordenada |
| `bonusShow` | grafia de cada palavra extra, na mesma posição que em `bonus` |
| `difficulty` | medida de dificuldade entre 0 e 1, três casas decimais; só para ordenar |
| `seed` | valor inicial do gerador (hexadecimal); sem sentido sem o gerador, que não é publicado |

Uma palavra de solução em `words`:

| Campo | Conteúdo |
| --- | --- |
| `w` | a forma |
| `show` | grafia real, como aparece na lista de palavras de “Resolvido.” (a grade mostra as letras das peças, sem acentos) |
| `r`, `c` | só em `kreuz`: linha e coluna da primeira letra, contadas a partir de 0 no canto superior esquerdo |
| `d` | só em `kreuz`: direção, `H` horizontal para a direita, `V` vertical para baixo |

Ordem das palavras de solução: nas páginas `kreuz`, primeiro a palavra-chave, depois por tamanho, da mais
longa para a mais curta; nas páginas `freisatz`, na ordem de exibição: palavras curtas primeiro, as de
mesmo tamanho em ordem alfabética, lidas da esquerda para a direita, linha por linha.

**Formável** significa: as letras da palavra podem ser colocadas com as peças, cada peça no máximo uma
vez.

Exemplo (página 1, com quebras de linha):

```json
{"page":1,"bogen":1,"kind":"kreuz","leit":"dia","tiles":["D","A","I"],"cols":3,"rows":3,
 "words":[{"w":"dia","r":0,"c":0,"d":"H","show":"dia"},
          {"w":"dai","r":0,"c":0,"d":"V","show":"daí"}],
 "bonus":["adi","ida"],"bonusShow":["adi","ida"],"difficulty":0.019,"seed":"0xbee663c026bf384"}
```

dá a grade

```
D I A
A . .
I . .
```

**Acentos:** a roda e a grade mostram as letras das peças (maiúsculas sem acentos, til nem cedilha);
a grafia com acentos (`show`, `bonusShow`) aparece onde as palavras são listadas.

### O livro (levels.json)

640 páginas em 40 capítulos de 16 páginas; a última página de cada capítulo (16, 32, …,
640) é um `freisatz`. 5,983 palavras de solução e 55,280 palavras extras.

### Os passatempos do dia (daily.json)

420 passatempos. O passatempo número *n* pertence ao dia 28 de setembro de 2026 mais
*n* − 1 dias; o número 1 é, portanto, segunda-feira, 28 de setembro de 2026. Depois do último, a
sequência recomeça. Os passatempos seguem um ritmo semanal:

| Dia da semana | Peças | Palavras de solução |
| --- | ---: | ---: |
| segunda-feira | 5 | 5–7 |
| terça-feira | 6 | 6–8 |
| quarta-feira | 6 | 7–9 |
| quinta-feira | 6 | 8–10 |
| sexta-feira | 7 | 9–11 |
| sábado | 7 | 12–14 |
| domingo (`freisatz`) | 6 | 7–9 |

3,481 palavras de solução e 30,526 palavras extras.

## curation/decisions.tsv — registro da revisão

Uma linha por decisão sobre uma forma, com o motivo. O registro não tem efeito sobre as listas; as
listas manuais abaixo têm. Se uma forma aparece mais de uma vez, vale a linha com o `pass` mais alto.

| Coluna | Conteúdo |
| --- | --- |
| `form` | a forma |
| `entscheidung` | decisão: `ok` continua de solução · `kein-ziel-ok` com razão não é de solução · `ziel-nein` palavra extra válida, nunca pedida · `ziel-pflicht` passa a ser de solução · `lesart-vorrang` continua de solução, leitura fixada · `kurzwort-ok` forma abreviada que vale como palavra comum |
| `grund` | motivo, em poucas palavras, em alemão |
| `pass` | rodada de revisão, `1`, `2`, … |

10,464 linhas; as 1 que se referem à lista de filtro não são publicadas.

## curation/*.txt — listas manuais

As listas que têm efeito quando as listas de palavras são construídas. Uma forma por linha, em
minúsculas, com as letras das peças ou com a grafia real (que é reduzida às letras das peças); `#` abre
um comentário até o fim da linha. Os comentários são notas de trabalho, em alemão, com o motivo; alguns
se referem a scripts e documentos das ferramentas não publicadas.

| Arquivo | Formato | Efeito |
| --- | --- | --- |
| `never-target.txt` | `forma  # motivo` | palavra extra válida, mas nunca de solução |
| `always-target.txt` | `forma  # motivo` | de solução, desde que a forma esteja na lista aceita |
| `spelling-priority.txt` | `forma  grafia  # motivo` | fixa a grafia de exibição `show` de uma forma (em `ziel.tsv` e `bonus.tsv`); a grafia precisa dar as mesmas peças que a forma |
| `fold-ok.txt` | `forma  # motivo` | forma que perde uma cedilha ou um til e então se lê como outra palavra, mas inofensiva (*manhã* → MANHA, *manha*); pode ser de solução |
| `reading-priority.txt` (só se existir) | `forma  lema[:classe]  # motivo` | fixa a primeira leitura de uma forma em `ziel.tsv` (lema e classe; a grafia `show` é escolhida à parte); nunca muda se uma forma é de solução |

## VERSION e SHA256SUMS

`VERSION` indica, em linhas `chave: valor`, o estado deste repositório (`date`), das listas de palavras
(`lexicon`), das fontes (`sources`) e a versão do app (`app`). `SHA256SUMS` contém a soma de verificação
SHA-256 de cada arquivo; para conferir: `shasum -a 256 -c SHA256SUMS` (macOS) ou
`sha256sum -c SHA256SUMS` (Linux).
