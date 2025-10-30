
# macOS/Unix terminal cheat sheet

## 📂 COMANDOS COMUNES (Unix/macOS)
---

Comando | Palabra completa           | Significado
--------|----------------------------|-------------------------------
cd      | change directory           | Cambiar de directorio
ls      | list                       | Listar archivos/carpetas
pwd     | print working directory    | Mostrar ruta del directorio actual
mkdir   | make directory             | Crear directorio
rmdir   | remove directory           | Eliminar directorio vacío
rm      | remove                     | Borrar archivo(s)
cp      | copy                       | Copiar
mv      | move                       | Mover o renombrar
touch   | (palabra entera)           | Crear archivo vacío / actualizar fecha
cat     | concatenate                | Mostrar contenido de archivos
less    | (palabra entera)           | Visualizar contenido paginado
head    | (palabra entera)           | Mostrar primeras líneas
tail    | (palabra entera)           | Mostrar últimas líneas
echo    | (palabra entera)           | Imprimir texto
man     | manual                     | Mostrar manual de un comando
whoami  | (palabra entera)           | Mostrar usuario actual
history | (palabra entera)           | Mostrar historial de comandos
open    | (palabra entera, macOS)    | Abrir archivo con la app por defecto
kill    | (palabra entera)           | Terminar un proceso

---

## 📖 EJEMPLOS BÁSICOS
---

# Navegación
```bash
pwd                # muestra dónde estoy
cd ~/Projects      # entrar en la carpeta Projects dentro de usuario
cd ..              # subir un nivel
ls -la             # listar archivos, con ocultos y detalles
```

# Crear, copiar, mover, borrar
```bash
mkdir prueba                # crear carpeta "prueba"
touch hola.txt              # crear archivo vacío
echo "Hola!" > hola.txt     # crear archivo con texto
cp hola.txt copia.txt       # copiar archivo
mv copia.txt renombrado.txt # renombrar/mover
rm renombrado.txt           # borrar archivo
rm -rf prueba               # borrar carpeta y todo su contenido (¡cuidado!)
```

# Ver contenido
```bash
open "archivo"       # abrir archivo  
cat hola.txt         # mostrar contenido completo
less hola.txt        # mostrar por páginas (q para salir)
head hola.txt        # primeras 10 líneas
tail hola.txt        # últimas 10 líneas
```

# Buscar
```bash
grep "Hola" hola.txt  # buscar palabra dentro del archivo
find . -name "*.txt"  # buscar todos los .txt desde carpeta actual
```

# Otros útiles
```bash
diskutil eject /Volumes/nombredeldisco # forzar expulsiones de forma segura
unzip archivo.zip                      # descomprimir archivo
unzip archivo.zip -d ~/Destino 
history                                # comandos recientes
clear                                  # limpiar pantalla (Ctrl+L)
man ls                                 # manual del comando ls
```

---
CC-BY-NC-4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 