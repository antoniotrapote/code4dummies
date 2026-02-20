# 1 Instalar Ollama con Homebrew

En tu Mac mini (Apple Silicon M4):
```bash
brew install ollama
```

Comprueba que se ha instalado:
```bash
ollama --version
```

Arrancar el servicio (si no arranca solo):
```bash
brew services start ollama
```

Verificar que responde:
```bash
ollama list
```

Si no hay modelos, simplemente mostrará lista vacía.

---

# 2 ¿Dónde guarda cosas Ollama?

Por defecto guarda modelos en:

```
~/.ollama
```

Ahí estarán:
* Los pesos del modelo (los archivos grandes)
* Configuración local

Puedes comprobarlo:
```bash
du -sh ~/.ollama
```

---

# 3 Desinstalar todo sin dejar restos y de forma completamente limpia.

## Paso A — Parar servicio

```bash
brew services stop ollama
```

## Paso B — Desinstalar Ollama

```bash
brew uninstall ollama
```

## Paso C — Eliminar modelos descargados

```bash
rm -rf ~/.ollama
```

Eso elimina absolutamente todos los modelos y configuraciones locales.

## Paso D — (Opcional) limpiar cache de brew

```bash
brew cleanup
```

---

# 4️⃣ ¿Queda algo escondido?

No.

Ollama no instala:

* Extensiones del sistema
* Drivers
* Launch agents raros
* Demonios ocultos fuera de brew

Todo queda en:

* Binario gestionado por Homebrew
* Carpeta `~/.ollama`

Es reversible al 100%.
