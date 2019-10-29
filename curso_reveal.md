# Introducción a Git

## Ángel L. Mateo (amateo at um.es)

---

# Referencias

- https://git-scm.com/book/es/v1/Empezando
- https://git-scm.com/book/es/v2

---

## Control de versiones
### ¿Qué es control de versiones? (VCS)

.right-column[
- Sistema que registra los cambios sobre un archivo o conjunto de archivos
- Recuperar versiones específicas
- Comparar cambios a lo largo del tiempo
- Ver quién introdujo qué modificación
]

---

### VCS centralizado

![Control de versiones centralizado](img/centralized.png){ width=10% }

???
- Servidor con todos los archivos versionados
- Clientes descargan los archivos desde servidor central
- Ventajas:
  - Todo el mundo conoce el último estado
  - Control detallado
  - Más sencillo
- Desventajas:
  - Punto único de fallo
