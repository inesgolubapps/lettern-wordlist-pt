# Lista de palavras do Lettern (português)

As listas de palavras e os dados dos passatempos do livro em português do **Lettern**, um passatempo de
palavras tranquilo para iPhone da Tickwork, publicados sob a licença
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.pt-br).

Estado 2026-11-24 · listas `pt-2026-11-20+sha256:f65d68400f3a` · Lettern 1.3.0 ·
o livro em alemão: <https://github.com/inesgolubapps/lettern-wortliste>

No Lettern, as palavras se formam arrastando o dedo sobre uma roda de letras, e com elas se preenche
uma pequena grade de palavras cruzadas. Quais palavras um passatempo pede e quais aceita como palavras
extras está neste repositório, junto com cada página do livro e cada passatempo do dia. Os dados vêm
de fontes de acesso aberto, entre elas o Wiktionary e o wordfreq, e por isso estão, como elas, sob
CC BY-SA 4.0.

## Conteúdo

| Arquivo | Conteúdo | Tamanho |
| --- | --- | --- |
| `data/ziel.tsv` | vocabulário de solução: palavras que um passatempo pode pedir, com grafia, forma básica, classe e frequência | 9,011 formas em 12,837 linhas |
| `data/bonus.tsv` | palavras aceitas: cada forma que vale como palavra extra, com sua grafia | 312,253 formas |
| `data/levels.json` | o livro: cada página com suas peças, grade, palavras de solução e palavras extras | 640 páginas em 40 capítulos |
| `data/daily.json` | os passatempos do dia, no mesmo formato | 420 passatempos |
| `curation/decisions.tsv` | registro da revisão palavra por palavra: uma linha por decisão, com o motivo | 10,464 linhas |
| `curation/never-target.txt` | palavras válidas que nunca são pedidas, com o motivo | |
| `curation/always-target.txt` | palavras de solução, mesmo que uma regra as deixasse de fora | |
| `curation/spelling-priority.txt` | grafias de exibição fixadas à mão (*faca*, *marco*, *trança*) | |
| `curation/fold-ok.txt` | formas que perdem o til ou a cedilha e mesmo assim podem ser pedidas (*manhã* → MANHA) | |
| `SOURCES.md` | cada fonte com versão, soma de verificação e licença | |
| `FORMAT.md` | as colunas e os campos de cada arquivo | |
| `LICENSE` | o texto jurídico da CC BY-SA 4.0 | |
| `VERSION`, `SHA256SUMS` | estado e somas de verificação de cada arquivo | |

Os nomes de arquivo (`ziel.tsv`, “ziel” = objetivo em alemão) e de coluna seguem o repositório alemão,
para que as mesmas ferramentas leiam os dois. Como são construídos está em [FORMAT.md](FORMAT.md).

## Quais palavras valem

- **Um livro para o Brasil e para Portugal.** As **palavras de solução** são palavras do dia a dia
  **nos dois países**, na forma básica ou em uma forma comum, como *casas* ou *comeu*. Só elas são
  pedidas. Para isso, cada uma passa por uma prova de variedade: sua frequência nas legendas
  brasileiras e nas portuguesas do OpenSubtitles (FrequencyWords) não pode ser muito diferente. Palavras
  de um só país (*ônibus*, *autocarro*) valem como palavras extras, nunca são pedidas.
- **Palavras extras** são outras palavras da lista do Lettern: formas portuguesas do Wiktionary de 3 a
  10 letras, também flexionadas ou raras, menos as que filtramos (veja abaixo). São aceitas, nunca
  pedidas. Valem as duas grafias atuais do Acordo Ortográfico de 1990 (*fato* e *facto*, *contato* e
  *contacto*); as grafias anteriores a 1990 (*acção*, *óptimo*) não valem.
- As formas verbais de *vós* (*amastes*, *falais*), os mais-que-perfeitos simples raros (*fizera*,
  *estivera*) e as palavras estrangeiras com k, w ou y (*show*, *karma*) valem só como palavras extras,
  nunca são pedidas.
- As **peças e a grade não têm acentos, til nem cedilha**: a peça A vale para A, Á, Â, Ã e À; a peça C,
  para C e Ç. *Coração* fica na grade como CORACAO. A grafia correta, com acentos, aparece onde as
  palavras são listadas (depois de “Resolvido.”, na lista de palavras extras) e ao consultá-las.
- Quando duas grafias dão as mesmas peças (*esta*/*está*, *avó*/*avô*), são uma só forma; a grafia
  exibida é a brasileira e, entre várias, a mais frequente, salvo correções à mão. Quando a forma sem
  cedilha ou til se lê como outra palavra corrente (*força* → FORCA), a palavra nunca é pedida.
- Não valem nomes próprios, abreviaturas, palavras com hífen, apóstrofo ou espaço (*guarda-chuva*,
  *dá-lo*) nem palavras com menos de três letras. Os palavrões mais fortes e os insultos contra grupos
  não valem, nem as suas derivações. Algumas palavras que têm, além de um sentido vulgar ou ofensivo, um
  sentido neutro (*rapariga*, “moça” em Portugal; *bicha*, “fila” em Portugal e verme) continuam valendo
  como palavras extras, mas nunca são pedidas.

## Atribuição

Os dados derivam destas obras. Arquivos, versões e somas de verificação em [SOURCES.md](SOURCES.md).

1. **Wiktionary em português (Wikcionário)** – das autoras e dos autores do Wiktionary em português,
   <https://pt.wiktionary.org>, legível por máquina graças ao kaikki.org com o wiktextract (Tatu Ylonen),
   <https://kaikki.org/ptwiktionary/>. Licença: CC BY-SA 4.0.
2. **Wiktionary em inglês, verbetes em português** – das autoras e dos autores do Wiktionary em inglês,
   <https://en.wiktionary.org>, via kaikki.org / wiktextract, <https://kaikki.org/dictionary/Portuguese/>.
   Licença: CC BY-SA 4.0 (também GFDL; usamos a CC BY-SA 4.0).
3. **wordfreq** – de Robyn Speer, <https://github.com/rspeer/wordfreq>. Licença dos dados: CC BY-SA 4.0.
   As frequências do português incluem legendas do projeto **OpenSubtitles**
   (<http://www.opensubtitles.org/>) via OPUS, do Brasil e de Portugal, além de Wikipédia, notícias, web
   e Twitter; sem livros (sem o Google Books Ngram).
4. **FrequencyWords** – de Hermit Dave, <https://github.com/hermitdave/FrequencyWords>, contagens do
   OpenSubtitles 2018, uma lista para o Brasil e uma para Portugal. Licença do conteúdo: CC BY-SA 4.0.
   Usado para a prova de variedade e para escolher a grafia exibida.

Estas obras são oferecidas por seus autores no estado em que se encontram; vale a limitação de
responsabilidade da sua licença (para a CC BY-SA 4.0, a seção 5, veja [LICENSE](LICENSE)).

## O que mudamos

Os arquivos foram elaborados a partir das fontes; as alterações estão indicadas abaixo, conforme a
seção 3(a)(1)(B) da licença:

- **Extraído.** Do Wiktionary, só verbetes da língua portuguesa: lema, classe, formas e marcas
  (vulgar, pejorativo, arcaico, regional, grafia anterior a 1990 …). Sem definições.
- **Reduzido às letras das peças.** Cada forma se escreve com as letras das peças: as letras perdem acentos, til e cedilha
  (á â ã à é ê í ó ô õ ú ü ç → a a a a e e i o o o u u c). A grafia real fica na coluna `show`. Se
  várias grafias dão a mesma forma (*esta*/*está*), é uma só forma, e `show` é a grafia escolhida para
  exibir a palavra: a brasileira e, entre várias, normalmente a mais frequente nas legendas brasileiras,
  salvo correções à mão.
- **Filtrado.** Ficam de fora nomes próprios, abreviaturas, formas com hífen, apóstrofo ou espaço,
  grafias anteriores a 1990 e os palavrões, as ofensas e as palavras sexuais mais fortes (veja “Não
  incluído”), também as suas derivações; as que têm além disso um sentido neutro ficam como palavras
  extras que nunca são pedidas.
- **Combinado.** A frequência de cada forma (coluna `zipf`) vem do wordfreq; a prova de variedade e a
  escolha da grafia exibida usam as contagens do FrequencyWords.
- **Selecionado por frequência.** As palavras de solução são formas com um sentido neutro e comum no
  Brasil e em Portugal, acima de um limiar de frequência e aprovadas na prova de variedade.
- **Revisado.** As formas de solução foram revisadas uma a uma; o que foi retirado, acrescentado ou
  corrigido está em `curation/`, com o motivo.
- **Passatempos gerados.** `levels.json` e `daily.json` foram gerados a partir das listas com nosso
  próprio programa. A partir do capítulo 3, as palavras-chave saem muitas vezes de nossas próprias
  listas de temas.

## Licença

Os dados deste repositório estão sob a licença **Creative Commons Atribuição-CompartilhaIgual 4.0
Internacional (CC BY-SA 4.0)**: <https://creativecommons.org/licenses/by-sa/4.0/deed.pt-br>. O texto
jurídico completo está em [LICENSE](LICENSE) (obtido em 2026-10-01 de
<https://creativecommons.org/licenses/by-sa/4.0/legalcode.txt>).

É permitido copiar, modificar e compartilhar os dados, também para fins comerciais, desde que os
autores sejam citados, as alterações sejam indicadas e a nova versão seja compartilhada sob a mesma
licença ou uma compatível.

## Reutilização

Esta linha cita todos os autores e pode ser copiada como está:

```
"Lista de palavras do Lettern (português)" da Tickwork, estado 2026-11-24, https://github.com/inesgolubapps/lettern-wordlist-pt, sob CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Derivada do Wiktionary (autoras e autores do Wikcionário em português e do Wiktionary em inglês, via kaikki.org/wiktextract, Tatu Ylonen), do wordfreq (Robyn Speer) com dados do OpenSubtitles e do FrequencyWords (Hermit Dave), CC BY-SA 4.0.
```

Quem tiver alterado os dados deve dizer o que mudou, por exemplo “reduzido a palavras de cinco letras”.

## Sinalizar um erro

Falta uma palavra, ela está escrita de forma errada ou não combina com um passatempo? Há três caminhos:

- uma issue neste repositório: <https://github.com/inesgolubapps/lettern-wordlist-pt/issues>
- no app: quando a página estiver resolvida, toque na palavra e escolha “Sinalizar”
- por e-mail para inesgolubapps@gmail.com

Ajudam a palavra e, em um passatempo, o número da página ou a data do passatempo do dia. As correções
chegam ao app e a este repositório em uma versão posterior.

## Não incluído

- **O código.** O código do app e as ferramentas que constroem estes arquivos não fazem parte deste
  repositório nem da licença. A licença cobre os dados.
- **A lista de filtro.** Ao construir as listas, outra lista separa palavrões, ofensas e palavras
  sexuais, com base nas marcas do Wiktionary e em revisão manual; uma lista pública de palavras ofensivas
  serviu só como apoio à revisão (veja SOURCES.md). Essa
  lista não faz parte dos dados: os arquivos de filtro não são publicados, nem aqui nem com o app. Os
  homônimos e as palavras de duplo sentido que admitimos podem aparecer nos dados. Por isso
  `curation/decisions.tsv` omite as 1 linhas que se referem a ela.
- O nome do app, suas imagens, sons, fontes tipográficas e textos.

## Sem garantia

Os dados foram reunidos para um jogo, não como dicionário nem como corretor ortográfico. São oferecidos
no estado em que se encontram, sem garantia de exatidão ou completude; pode haver erros e entradas
discutíveis. A responsabilidade pelo seu uso fica excluída na medida em que a lei o permitir (seção 5 da
licença).
