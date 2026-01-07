# Apuntes Fundamentos de Programación

Nueva versión de los apuntes de Fundamentos de Programación, actualizados y más fáciles de modificar.

## Instalación y uso local

1. Cloná este repositorio en tu máquina local.
2. Instalá `mdbook` si no lo tenés instalado:

- macOS: `brew install mdbook`
- Linux:
  - Instalá Rust con: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
  - Luego, instalá mdBook con: `cargo install mdbook`
- Windows: ???

Si ninguna funciona, seguir las instrucciones oficiales en [mdBook - Getting Started](https://rust-lang.github.io/mdBook/guide/installation.html).

3. Una vez instalado, navegá al directorio del proyecto y ejecutá: `mdbook serve`.
4. En tu navegador, abrí `http://localhost:3000` para ver los apuntes.

## Estructura del proyecto

```
.
├── book.toml          # Configuración de mdbook
├── src/               # Todo el contenido del curso va acá
│   ├── SUMMARY.md     # Tabla de contenidos (define la estructura del libro)
│   └── vectores.md    # Ejemplo: organizado por temas
└── book/              # Salida generada (ignorar)
```

### Agregar nuevo contenido

1. Creá un nuevo archivo Markdown en la carpeta `src/`, por ejemplo `vectores.md`.
2. Editá `src/SUMMARY.md` para agregar nuevas secciones o capítulos.

```markdown
# Summary

- [Punteros](./punteros.md)
- [Vectores](./vectores.md) # <- Agregar esta línea
```

**Importante:** Si un archivo no está listado en `SUMMARY.md`, no va a aparecer en el libro generado.

3. Probar localmente con

```bash
mdbook serve
```

Tus cambios se van a recargar automáticamente en http://localhost:3000

## Consejos

- Usá enlaces relativos entre páginas: `[ver punteros](./punteros.md)`
- Los bloques de código soportan resaltado de sintaxis: ```c
- Las imágenes van en `src/` y se referencian con `![alt](./ruta/a/imagen.png)`
- La indentación en `SUMMARY.md` crea capítulos anidados
