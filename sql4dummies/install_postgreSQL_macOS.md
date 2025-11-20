## 1. Instalar PostgreSQL en macOS usando Homebrew

```bash
brew install postgresql
```

## 2. Iniciar el servicio de PostgreSQL

### Iniciar PostgreSQL como servicio automático en macOS
Esto activará PostgreSQL para que se inicie automáticamente al arrancar el sistema.
```bash
brew services start postgresql

# Si quiere indicar una versión específica de PostgreSQL, use:
brew services start postgresql@NN
# Siendo NN la versión deseada
``` 

### Detener PostgreSQL como servicio automático en macOS
```bash
brew services stop postgresql
```

### Iniciar PostgreSQL manualmente en macOS
```bash
/opt/homebrew/opt/postgresql@14/bin/pg_ctl -D /opt/homebrew/var/postgresql@14 start
```
### Detener PostgreSQL manualmente en macOS
```bash
/opt/homebrew/opt/postgresql@14/bin/pg_ctl -D /opt/homebrew/var/postgresql@14 stop
```

## Comprobar el estado de PostgreSQL en macOS
```bash
brew services list
```
salida esperada:
```
Name          Status  User Plist
postgresql    started your_username /opt/homebrew/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```

## Desinstalar PostgreSQL en macOS usando Homebrew
```bash
brew uninstall postgresql
```

Si quiere eliminar también los datos y configuraciones:
```bash
rm -rf /opt/homebrew/var/postgresql@NN
```


---

CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 