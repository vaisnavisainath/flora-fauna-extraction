# Extraction of Indian Cultural Elements Using RAG

Extraction of Indian flora and fauna from six Indian literary texts using Retrieval-Augmented Generation (RAG).

- **Author:** Vaisnavi Sainath
- **Semester:** Monsoon Semester 2026
- **Affiliation:** Department of Humanities and Social Sciences, Indian Institute of Technology (Indian School of Mines), Dhanbad
- **Project webpage:** https://YOUR-USERNAME.github.io/YOUR-REPO/

## About

Indian literature names plants and animals constantly: the tree under which a scene is set, the bird heard at dusk, the flower offered in worship. This project takes flora and fauna as a first category of Indian cultural elements and uses RAG to collect them from six books. For each book, a language model was given retrieved passages and asked to list the flora and the fauna they name.

**Research question:** What flora and fauna can retrieval-augmented generation extract from Indian literary texts, and how reliable and complete are the resulting lists?

## Corpus

| Book | Author | Form | Flora | Fauna |
|---|---|---|---|---|
| Bengal Peasant Life | Lal Behari Day | Novel of rural life | 44 | 22 |
| Folk-Tales of Bengal | Lal Behari Day | Folk tales | 18 | 27 |
| The Palace of Illusions | Chitra Banerjee Divakaruni | Novel (Mahabharata retelling) | 25 | 21 |
| Kari the Elephant | Dhan Gopal Mukerji | Children's novel | 8 | 25 |
| Indian Tales of the Great Ones | Cornelia Sorabji | Retold stories | 9 | 11 |
| The Golden Threshold | Sarojini Naidu | Poems | 16 | 23 |
| **Total** | | | **120** | **129** |

## Repository contents

| File | Description |
|---|---|
| `flora_fauna.py` | Two dictionaries, `flora_RAG_extraction` and `fauna_RAG_extraction`, mapping each book to its list of extracted entries (249 entries) |
| `index.html` | Project webpage: lists explorer, charts, results and discussion |
| `README.md` | This file |

## Usage

Requires Python 3. No external libraries are needed.

Print a summary of the extraction:

```bash
python flora_fauna.py
```

Load the lists in your own code:

```python
import flora_fauna as ff

print(len(ff.flora_RAG_extraction))                             # 6 books
print(sum(len(v) for v in ff.flora_RAG_extraction.values()))    # 120 flora entries
print(sum(len(v) for v in ff.fauna_RAG_extraction.values()))    # 129 fauna entries

book = "The Golden Threshold (Sarojini Naidu)"
names = [e.split(" (")[0] for e in ff.flora_RAG_extraction[book]]
print(names[:3])    # ['Lotus', 'Henna', 'Neem']
```

Entries are shown as the model returned them. Many include local names, varieties or scientific names in brackets, and some join several names with a slash (for example `Asvatha / Peepal (Ficus religiosa)`).

## Viewing the webpage

Open `index.html` in a browser, or view it online through GitHub Pages:

1. Go to **Settings → Pages** in this repository.
2. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then save.
3. After a minute the site is live at the address given at the top of the Pages settings.

## Limitations

- The lists were not compared with a manual annotation, so precision and recall are not reported.
- Names are not standardised, and entries are names only, without the passage or meaning in the text.
- Six books are a small sample of Indian literature.

## Reference

Lewis, P. et al. (2020). Retrieval-augmented generation for knowledge-intensive NLP tasks. *Advances in Neural Information Processing Systems*, 33.
