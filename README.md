# Competitive Programming Scripts

> [!IMPORTANT]
> Solo probado en sistemas UNIX.
> Si lo estás haciendo desde Windows y algo falla, abre una issue.

Repositorio para los scripts que usaremos en los concursos y para generar la referencia para llevarla impresa.

Con `generate-reference.py`, generas el archivo en [`REFERENCE.md`](./REFERENCE.md).
Adicionalmente, en cada push se despliega automáticamente el `Script reference` que puedes ver en: [REFERENCE.pdf](jhonatandczel.github.io/.cp-scripts/reference.pdf).

## Estructura

- **bin**: Aquí van los scripts finales, desde donde los leerá el `path`.
- **scripts**: Carpeta con el código fuente de los scripts. Si quieres crear un script, agrega una nueva carpeta dentro.
- **tools**: Herramientas para empaquetar los scripts a `bin` (`build_scripts.py`) y para generar la referencia (`generate-reference.py`).

## Agregar un script

1. Crea un nuevo directorio en `scripts` y agrega tu archivo ahí.
2. Para la descripción del script, usa comentarios `# >` de la forma:

   ```sh
   #!/usr/bin/env zsh

   # > Script que dice hola mundo
   # > esta es su descripción

   echo "Hola mundo"
   ```

3. Ejecuta el comando `build_scripts.py` (desde el directorio principal) para exportar los scripts:

   ```sh
   ./tools/build_scripts.py
   ```

4. ¡Listo! Sube los cambios al repositorio y se empezará el despliegue para ver el PDF. Si quieres generar el `REFERENCE.md` manualmente:

   ```sh
   ./tools/generate_reference.py
   ```

## Observaciones

- Para scripts en otros lenguajes, incluye en la primera línea el shebang (`#!`) referenciando el intérprete.
- Los scripts van en la carpeta `scripts`. Si quieres agregar un script, crea un nuevo directorio con el nombre de tu script.
- Para evitar conflictos entre los nombres de los comandos, todos los comandos finales iniciarán con un `cps-`.
  - **Ejemplo**: `compile_exercise.sh` será llevado a `/bin` como: `cps-compile_exercise`.
  - En caso de que haya dos scripts con el mismo nombre, se usará su extensión para distinguirlos.
- Si necesitas que tu script use algún archivo, inclúyelos dentro de la carpeta que contiene a tu script. Si es un recurso compartido, deberías incluirlo en un directorio en `/resources`.
- Para referenciar algún archivo, usa siempre una ruta relativa al directorio home.
  - **Ejemplo:** Para referenciar `template-1.cpp` -> `~/.cp-scripts/public/template-1.cpp`.
    ciar `template-1.cpp` -> `~/.cp-scripts/public/tempate-1.cpp`
