CONTEXTO
La bóveda de Obsidian en Android es un repo git que se publica a GitHub, no una carpeta que se sincronice sola.
- Bóveda: /storage/emulated/0/Download/arvhicos/02_NOTAS_OBSIDIAN
- Remoto: https://github.com/ahernandezte-oss/Obsidian (rama main)
- Plugin: git-sync (auto-commit 5 s, auto-pull 30 s)

COMPORTAMIENTO CLAVE
El plugin solo hace commit+detección cuando Obsidian está abierto y detecta el cambio. Si un agente escribe .md directamente en el disco, el plugin NO los ve: quedan en el teléfono, GitHub no se entera y los demás dispositivos no ven nada. Un archivo visible en disco no significa publicado.

PROTOCOLO OBLIGATORIO TRAS CADA ARCHIVO
1. git -C <bóveda> fetch origin
2. git -C <bóveda> log --oneline HEAD..origin/main   (qué llegó antes)
3. git -C <bóveda> diff --name-only HEAD...origin/main  (¿choca con lo mío?)
4. git -C <bóveda> rebase origin/main
5. git -C <bóveda> add -A <carpeta de la materia>
6. git -C <bóveda> commit -m "<MATERIA>: qué cambió"
7. git -C <bóveda> push origin main
8. Verificar: sha256 local == sha256 en origin/main del archivo, y HEAD == origin/main

PROHIBIDO (rompe la sincronización de los otros dispositivos)
- git push --force / --force-with-lease
- git reset --hard ni commit --amend sobre commits ya publicados
- push sin fetch+rebase antes
- Mezclar materias en un mismo commit (cada materia va sola)
- Añadir el data.json del plugin git-sync al repo: contiene el token de GitHub

SI HAY CONFLICTO
Detenerse, no forzar nada, reportar el archivo y las líneas en conflicto.

SI EL OTRO DISPOSITIVO NO VE LOS CAMBIOS AUNQUE EL PUSH OK
Comprobar en este orden: (a) que abrió la bóveda en la ruta correcta y no una copia duplicada del arbol arvhicos; (b) que en el otro dispositivo existe una sola carpeta .obsidian; (c) forzar "Git Sync: Pull", o cerrar y reabrir Obsidian para refrescar el índice.

REGLA
Nunca cierres una tarea diciendo que el archivo "ya está subido" sin haber ejecutado el push y verificado el hash contra origin/main.