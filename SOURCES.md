# Fontes, versões e licenças

Estado 2026-11-24 · listas `pt-2026-11-20+sha256:f65d68400f3a` · fontes de 2026-11-20

Cada arquivo das fontes foi fixado pela sua soma SHA-256; quem construir as listas com os mesmos
arquivos e as mesmas versões das ferramentas, regras, parâmetros e listas de revisão obtém, byte por
byte, os mesmos dados. As citações das licenças foram lidas na fonte indicada.

## Fontes que entram nas listas

### 1. Wiktionary em inglês, verbetes em português (kaikki.org / wiktextract)

- Arquivo: `enwiktionary-Portuguese.jsonl.gz`
- URL: https://kaikki.org/dictionary/Portuguese/kaikki.org-dictionary-Portuguese.jsonl.gz
- Versão: dump do enwiktionary de 2026-10-01, extraído em 2026-10-30
- SHA-256: `0db87ddd508032c4e986fe818826801c9b167b2ee4f8315763166f0fa4014480`
- Licença: CC BY-SA 4.0 e GFDL. Wikimedia: “dual-licensed … under both the Creative Commons
  Attribution-ShareAlike 4.0 International License … and the GNU Free Documentation License”
  (https://en.wiktionary.org/wiki/Wiktionary:Copyrights). kaikki.org: “This data is made available under
  the same licenses as Wiktionary - both CC-BY-SA and GFDL.”
- Uso: lemas, classes, formas, marcas de registro (vulgar, pejorativo, obsoleto …) e de região (Brasil,
  Portugal), as indicações de grafia europeia ou brasileira no cabeçalho do verbete e as glosas que
  marcam grafias anteriores a 1990 (“pre-reform spelling of …”) e as grafias duplas do Acordo
  (“European/Brazilian Portuguese standard spelling of …”).

### 2. Wiktionary em português (Wikcionário), verbetes “Português” (kaikki.org / wiktextract)

- Arquivo: `ptwiktionary-Portugues.jsonl.gz`
- URL: https://kaikki.org/ptwiktionary/Portugu%C3%AAs/kaikki.org-dictionary-Portugu%C3%AAs.jsonl.gz
- Versão: dump do ptwiktionary de 2026-10-01, extraído em 2026-11-02
- SHA-256: `d540b3e0a866ec96fd6fc4a941602bc438c37429a888e33827ccd7e957d9b627`
- Licença: Wikcionário, rodapé de cada página: “Creative Commons Atribuição-CompartilhaIgual”.
  kaikki.org: “This data is made available under the same licenses as Wiktionary - both CC-BY-SA and
  GFDL.”
- Uso: segunda opinião sobre lemas e formas (conjugações completas), as categorias de registro e de
  região de cada acepção (“Português brasileiro”, “Português lusitano”, “Pejorativo”, “Obscenidade”,
  “Gíria”).

kaikki.org e wiktextract: Tatu Ylonen, “Wiktextract: Wiktionary as Machine-Readable Structured Data”,
LREC 2022, pp. 1317-1325.

### 3. wordfreq (Robyn Speer), português `large`

- Pacote: wordfreq 3.1.1, wheel SHA-256 `4b1c6ecffc6198be3396d5cf871c4423ca71c907c231348d352dd54d62b97473`
- Arquivo de dados: `wordfreq/data/large_pt.msgpack.gz`, SHA-256
  `7d764586bca6262f554d5fa77ad8e6841ef42534776e70558065140853660ce2`
- Licença: “`wordfreq` is freely redistributable under the Apache license (see `LICENSE.txt`), and it
  includes data files that may be redistributed under a Creative Commons Attribution-ShareAlike 4.0
  license” (https://github.com/rspeer/wordfreq#license). OpenSubtitles 2018 via OPUS: “may be used with
  attribution to OpenSubtitles.” A lista portuguesa se baseia em Wikipédia, legendas (do Brasil e de
  Portugal juntas), notícias, web e Twitter; não contém livros (nem o Google Books Ngram) nem SUBTLEX.
- Uso: a frequência de cada forma (coluna `zipf`) e os limiares do vocabulário de solução.

### 4. FrequencyWords (Hermit Dave), `pt_br_full.txt` (Brasil)

- Arquivo: `frequencywords-pt_br_full.txt`
- URL: https://raw.githubusercontent.com/hermitdave/FrequencyWords/525f9b560de45753a5ea01069454e72e9aa541c6/content/2018/pt_br/pt_br_full.txt
- Versão: git 525f9b5 (2022-02-07), conteúdo OpenSubtitles 2018, legendas do Brasil
- SHA-256: `533b3abaab3b1ea9cec7a150fc8aaf8d428c6f241979cc2224b7ee82f8a369b2`
- Licença: “MIT License for code. CC-by-sa-4.0 for content.” (https://github.com/hermitdave/FrequencyWords)
- Uso: prova de variedade (com a fonte 5) e grafia exibida: a frequência brasileira decide entre as
  grafias que dão as mesmas peças.

### 5. FrequencyWords (Hermit Dave), `pt_full.txt` (Portugal)

- Arquivo: `frequencywords-pt_full.txt`
- URL: https://raw.githubusercontent.com/hermitdave/FrequencyWords/525f9b560de45753a5ea01069454e72e9aa541c6/content/2018/pt/pt_full.txt
- Versão: git 525f9b5 (2022-02-07), conteúdo OpenSubtitles 2018, legendas de Portugal
- SHA-256: `21ac5ba5840001d522f2a7b91cc7cd0b25d24a8dcea3ecf997277662859b8f2f`
- Licença: como a fonte 4.
- Uso: prova de variedade: as frequências por milhão de uma palavra de solução nas duas listas de
  legendas não podem diferir demais (com suavização: (máx + 1) / (mín + 1) por milhão abaixo de 8; os gerúndios seguem a prova do seu verbo, porque *fazendo* é a mesma palavra nos dois países, e *você* é palavra de solução por decisão à mão).

## Fonte só para a construção (não faz parte dos dados)

### 6. LDNOOBW, português

- Arquivo: `ldnoobw-pt.txt`
- URL: https://raw.githubusercontent.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words/5faf2ba42d7b1c0977169ec3611df25a3c08eb13/pt
- Versão: git 5faf2ba (2020-07-13)
- SHA-256: `05ef524b0bb7f83f87257f6ec4dabf70e16b8bb6930f769fb93deaf608ff196d`
- Licença: “This work is licensed under a Creative Commons Attribution 4.0 International License”,
  “© 2012–2020 Shutterstock, Inc.”
- Uso: só uma marca na revisão de palavras ofensivas; não bloqueia nada por si mesma (a lista contém
  também *cerveja*, *aranha*, *amador*) e não é publicada.

## Não utilizadas

Não são usadas, nem como filtro nem como contraprova: **MorphoBr** (etiqueta Apache, mas derivado de
FreeLing/LABEL-LEX sob GPLv3 e de Unitex-PB sob LGPLLR), **SUBTLEX-PT-BR** (CC BY-NC-ND), **SUBTLEX-PT**
(só para pesquisa), **CETEMPúblico** (uso comercial vedado), **VERO** (pt-BR), Natura (pt-PT) e as
demais listas Hunspell/Aspell (LGPL/MPL/GPL), o VOLP, o VOC e o LexPorBR (nenhuma licença encontrada).
