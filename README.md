# Qminer Quant Hackaton Kick-off

V tomto repozitáři najdeš vše potřebné k odladění tvého modelu, aby tě odevzdávací systém ničím nepřekvapil.

Odevzdávací systém beží na webu [hyperion.felk.cvut.cz](https://hyperion.felk.cvut.cz/).

## Struktura repozitáře
* data/train_dataset.csv obsahuje trénovací data
* problem_definition_cs.md obsahuje zadání úlohy včetně popisu dat
* runtime.yml obsahuje runtime prostředí
* src/environment.py obsahuje evaluační smyčku, která běží v odevzdávacím systému
* src/evaluate.py skript pro evaluaci Tvého modelu
* src/model.py obsahuje model, který odevzdáváš (defaultně random)

## Runtime prostředí

Soubor runtime.yml obsahuje balíky, které budou dostupné při evaluaci. Vřele doporučujeme toto prostředí replikovat lokálně.

1. Nainstaluj si nástroj miniconda: https://docs.conda.io/en/latest/miniconda.html
2. Importuj environment: `conda env create -f runtime.yml`
3. Aktivuj (po každém restartu shellu) enviroment: `conda activate hackathon` 

Vývojová prostředí (IDE) často umí s conda environmenty pracovat (například PyCharm).

Pro ověření funčnosti můžeš rovnou spustit evaluaci modelu, který sází náhodně: `python evaluate.py`

Pokud pro své řešení potřebuješ knihovnu, které v runtime.yml není, napiš nám, pokusíme se ti vyhovět.

## Vlastní řešení

Třída, kterou budeš odevzdávat, se musí jmenovat Model a musí obsahovat implementaci funkce place_bets(self, [opps](https://github.com/IDA-CTU/hackathon/blob/master/problem_definition_cs.md#dataframe-s%C3%A1zka%C5%99sk%C3%BDch-p%C5%99%C3%ADle%C5%BEitost%C3%AD), [summary](https://github.com/IDA-CTU/hackathon/blob/master/problem_definition_cs.md#dataframe-se-shrnut%C3%ADm), [inc](https://github.com/IDA-CTU/hackathon/blob/master/problem_definition_cs.md#dataframe-inkrement%C3%A1ln%C3%ADch-dat)) vracející [sázky](https://github.com/IDA-CTU/hackathon/blob/master/problem_definition_cs.md#dataframe-s%C3%A1zek).

Bližší info najdeš v samotném [zadání](https://github.com/IDA-CTU/hackathon/blob/master/problem_definition_cs.md).

## Evaluace

Evaluace v odevzdávacím systému probíhá na skrytých (testovacích) datech. Trénovací [data](https://github.com/IDA-CTU/hackathon/blob/master/data/training_data.csv) obsahují zápasy ze sezón 2000-2010. Testovací data obsahují zápasy ze sezón 2011-2016. V první iteraci [evaluační smyčky](https://github.com/IDA-CTU/hackathon/blob/master/src/environment.py#L37) obdržíš jako [inkrement](https://github.com/IDA-CTU/hackathon/blob/master/problem_definition_cs.md#dataframe-inkrement%C3%A1ln%C3%ADch-dat) všechna trénovací data.
