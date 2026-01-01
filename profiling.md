In informatica, il profiling è un'analisi delle prestazioni di un programma software, eseguita mentre il programma è in funzione (analisi dinamica).
Lo scopo principale è individuare quali parti del codice sono inefficienti, permettendo allo sviluppatore di ottimizzarle invece di "tirare a indovinare" su cosa rallenta il sistema.

#### Profiling con cProfile (Built-in)

Ordina i risultati per tempo di esecuzione
```
python -m cProfile -s time script.py
```

Salva il risultato su file
```
python -m cProfile -s time -o output.prof script.py
```

Visualizza graficamente con SnakeViz
```
snakeviz output.prof
```

#### Profiling con line_profiler
Permette di analizzare ogni singola riga di codice
```
pip install line_profiler
```

1. Aggiungi il decoratore @profile sopra la funzione che vuoi analizzare (non serve importare nulla nello script, il tool lo riconoscerà automaticamente)
```
@profile
def la_mia_funzione_lenta():
    a = [i for i in range(100000)]  # Riga veloce
    time.sleep(2)                   # Riga lenta!
    return a
```

2. Esegui lo script con il comando kernprof
```
kernprof -l -v mio_script.py
```

#### Profiling con pyinstrument
pyinstrument permette di fare il profiling mostrando l'intero stacktrace in modo leggibile, in modo da analizzare l'intera catena di eventi.
```
pip install pyinstrument
```

Esegui e apri il file generato
```
pyinstrument -rhtml -o output.html cript.py
```
