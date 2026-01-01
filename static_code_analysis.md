

#### Analisi statica con Pylint
Analizza il codice e restituisce una serie di messaggi e un voto finale.
```
pip install pylint
```

Testa un file
```
pylint script.py
```

Testa un modulo
```
pylint module/
```

#### Genera diagrammi del codice con pyreverse
pyreverse è un tool gemello a pylint, che permette di creare diagrammi UML di file, moduli e progetto per mostrare graficamente le relazioni tra le diverse componenti del codice.
Ha bisogno di [Graphviz](https://graphviz.org/download/) installato.

Generazione del grafico UML per un modulo, i possibili formati sono png, jpg, svg, html.
```
pyreverse -o png -p output modulo/
```
verranno generati due file:
 - classes_output: diagramma delle classi
 - packages_output: diagramma dei pacchetti
