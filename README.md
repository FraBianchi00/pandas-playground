# pandas-playground

Progetto di apprendimento per padroneggiare pandas attraverso 4 notebook progressivi sul dataset Titanic. Parte della Fase 1 (Fondamenta) del mio percorso verso un portfolio Data Science.

## Obiettivo

Consolidare le operazioni fondamentali di pandas — caricamento, selezione, aggregazione, trasformazione e combinazione di DataFrame — su un dataset reale, costruendo un riflesso pratico prima di passare ai progetti di EDA e Machine Learning.

## Dataset

[Titanic](https://www.kaggle.com/competitions/titanic) — 891 passeggeri con informazioni demografiche, classe di viaggio, porto di imbarco e sopravvivenza. Dataset classico perché contiene tipi misti (numerici, categorici, testuali) e valori mancanti realistici.

## Struttura

```
pandas-playground/
├── data/                    # dataset grezzo (non versionato)
├── notebooks/
│   ├── 01_carica_e_guarda.ipynb
│   ├── 02_seleziona_e_filtra.ipynb
│   ├── 03_aggrega_e_raggruppa.ipynb
│   └── 04_trasforma_e_combina.ipynb
├── requirements.txt
└── README.md
```

## Contenuto dei notebook

### 01 — Carica e guarda
Primo contatto col dataset: `shape`, `columns`, `info()`, `dtypes`, `isna()`. Distinguere cosa è un problema (NaN in colonne critiche) da cosa è normale.

### 02 — Seleziona e filtra
Selezione di colonne (Series vs DataFrame, parentesi singole vs doppie), `.loc` e `.iloc`, maschere booleane, condizioni combinate con `&` `|` `~` e parentesi obbligatorie.

### 03 — Aggrega e raggruppa
`value_counts()` (con `dropna` e `normalize`), `groupby` singolo e multiplo, `.agg()` con named aggregation. Pattern `groupby(X)[Y].funz()` — X è il *chi*, Y è il *cosa*. Trucco della media su colonna binaria = proporzione di 1. Differenza tra `count` e `size`.

### 04 — Trasforma e combina
Creazione di colonne derivate con la gerarchia operazione vettoriale → `map` / `replace` → `np.where` → `apply`. Binning con `pd.cut` e `pd.qcut`. Combinazione di DataFrame con `concat` (axis 0 e 1) e `merge` (tutti e 4 i tipi di `how`, e il bug classico dei duplicati quando la chiave non è univoca).

## Cosa ho imparato

- **Series vs DataFrame**: la differenza concreta tra `df["col"]` e `df[["col"]]` e le implicazioni a valle.
- **Maschere booleane**: costruirle in modo pulito e combinarle senza ambiguità operatoriali.
- **Groupby come strumento di pensiero**: separare *chi* (la dimensione) da *cosa* (la metrica).
- **Gerarchia per trasformare colonne**: scegliere lo strumento più semplice che fa il lavoro, non il più flessibile.
- **Merge come JOIN relazionale**: prevedere mentalmente righe e match prima di lanciarlo, controllare `.shape` dopo.
- **Gotchas reali**: propagazione di NaN nei merge, differenza `map` vs `replace` sui valori non previsti, inclusività delle soglie nel binning, indici duplicati dopo `concat`.

## Setup

```bash
git clone https://github.com/FraBianchi00/pandas-playground.git
cd pandas-playground
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

Il dataset Titanic va scaricato da [Kaggle](https://www.kaggle.com/competitions/titanic) e posizionato in `data/titanic.csv`.

## Tecnologie

- Python 3.11
- pandas, numpy
- Jupyter Notebook

## Prossimo step

Con pandas-playground chiuso, il prossimo progetto è una **EDA completa** su un dataset pubblico sporco, con report finale e dashboard Streamlit. Parte della Fase 2 (Data Analysis & Visualization) del mio percorso.