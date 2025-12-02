# psql Display Options
Algunas opciones útiles para personalizar la salida en psql.

Muestra cada columna en una fila separada.
```bash
# \x = expanded display ; on | off
\x on 
```

```bash
# border 0 = no borders, border 1 = minimal, border 2 = full borders
\pset border 2
```

Adapta el formato de salida a la anchura del terminal.
```bash
# \pset format = output format
\pset format wrapped
```
