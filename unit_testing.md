#### Unit-test con pytest

1. Definisci funzioni o metodi da testare
```
# operazioni.py

def somma(a, b):
    return a + b
```

2. Crea i test
```
# test_operazioni.py
import pytest
from operazioni import somma

def test_somma_positiva():
    risultato = somma(2, 3)
    assert risultato == 5

def test_somma_negativa():
    assert somma(-1, -1) == -2
```

3. Esegui i test
```
pytest test_operazioni.py
```

Esegui tutti i test in tutti i file della directory corrente
```
pytest
```

Esegui solo gli ultimi test falliti
```
pytest --lf
```

Esegui solo i test che contengono la parola "somma"
```
pytest -k "somma"
```

Effettua più test con parametri diversi
```
@pytest.mark.parametrize("input_a, input_b, atteso", [
    (2, 3, 5),      # Caso 1
    (0, 0, 0),      # Caso 2
    (-1, 1, 0),     # Caso 3
    (100, 200, 300) # Caso 4
])
def test_somma_parametrizzata(input_a, input_b, atteso):
    assert somma(input_a, input_b) == atteso
```

#### Code coverage con pytest-cov
La code coverage ci dice quanto del nostro codice è coperto da test, puoi farla con pytest-cov
```
pip install pytest-cov
```

Verifica la copertura dei test presenti nella cartella tests
```
pytest --cov=tests
```

Genera un report in HTML
```
pytest --cov=. --cov-report=html
```

Forza il fail di pytest se la copertura è sotto una determinata percentuale (es. 80%)
```
pytest --cov=tests --cov-fail-under=80
```

Puoi ignorare determinate righe di codice dalla copertura con "# pragma: no cover"
```
def funzione_strana():
    # ... codice ...
    if condizione_impossibile:
        print("Questo non dovrebbe mai accadere")  # pragma: no cover
```
