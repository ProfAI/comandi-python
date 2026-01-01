La struttura tipica di un package è questa:
```
my_package/
├── LICENSE
├── pyproject.toml
├── README.md
├── src/
│   └── my_package/
│       ├── __init__.py
│       └── example.py
└── tests/
```

Il pyproject.toml è il file di configurazione in cui si specifica quale strumento usare per buildare il progetto
```
[project]
name = "my_package"
version = "0.0.1"
authors = [
  { name="ProfAI", email="prof@profession.ai" },
]
description = "A small example package"
readme = "README.md"
requires-python = ">=3.9"
classifiers = [
    "Programming Language :: Python :: 3",
    "Operating System :: OS Independent",
]
license = "MIT"
license-files = ["LICEN[CS]E*"]

[project.urls]
Homepage = "https://github.com/profai/my_project"
Issues = "https://github.com/profai/my_project"
```

Per buildare usiamo il tool build di python:
```
python3 -m build
```

Verrà creata una directory dist con 2 file:
 - file .whl: è un archivio zip con il codice organizzato esattamente come deve essere copiato nel computer dell'utente. 
 - file .tar.gz: è il codice compresso, viene usato come backup se il .whl non funziona.

Possiamo installare con pip:
```
pip install ./dist/nomefile.whl
```

#### Upload di test su pypi
```
python3 -m pip install --upgrade twine
```

Ci serve un token pypi che possiamo ottenere [da qui](https://test.pypi.org/account/login/?next=%2Fmanage%2Faccount%2F#api-tokens).

Ora possiamo usare il token per caricare il package su una repo di test pypi con twine
```
python3 -m twine upload --repository testpypi dist/*
```

Ora per installare il package possiamo usare questo, dove YOUR-USERNAME è l'username usato per la registrazione su pypi
```
python3 -m pip install --index-url https://test.pypi.org/simple/ --no-deps my_package-YOUR_USERNAME
```

#### Distribuzione su pypi
Se sei pronto per distribuire il tuo package a tutti, puoi usare sempre twine senza specificare la repository:
```
twine upload dist/* 
```

**Risorse**
1. [Packaging Python Projects](https://packaging.python.org/en/latest/tutorials/packaging-projects/)
