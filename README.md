# CLSC - Cross-Lingual Sentence Compression

Download data from OpenSub/EuroParl from the `/data` folder. Each folder has separate scripts for this.

We include a batch downloader for several languages. For specific languages:

`python download_langs.py en fr` for english-french parallel data

Fine-tuning of models can be seen in `finetune.py`.

## How to run

### 1. Download data

```bash
# europarl
cd data/europarl && python download.py
# opensubtitles
cd data/opensubtitles && chmod +x download_selection.sh && ./download_selection.sh
```


### 2. Train

#### CM -- Compression-token Model

```bash
python finetune_CLSC_CM.py
```

#### MM - Multiple Models per compression ratio

```bash
python finetune_CLSC_MM.py
```

### 3. inspect data and results

See the results in the [figures-and-tables](figures-and-tables) folder. E.g., the CM outputs are found in [`print_results_CLSC_CM_opensub.ipynb`](figures-and-tables/print_results_CLSC_CM_opensub.ipynb).

At the very end of these files, you can "peek" results with random indexes. Example output:

```python
index: 343
source
>>nob<< Your ankle seems to be fine. Just a mild sprain, so this should help. Great.

target
Åh gud.

baseline
Det ser ut til at ankelen din har det fint, bare en mild fordypning, så dette burde hjelpe.

0.5
Ankelen din virker bra.

0.6
Ankelen din virker bra, så dette hjelper.

0.7
Det er bare en mild forsvinning, så dette burde hjelpe.

```