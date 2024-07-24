# Ejercicios

## 25

Crea un nuevo usuario llamado "nuevo-usuario" en Ubuntu. Luego, inicia sesión con ese usuario y observa las diferencias y los permisos en comparación con el usuario principal. Utiliza los comandos como useradd, passwd, su, sudo, y ls para explorar los cambios y las capacidades del nuevo usuario.

## Ejemplo lectura de un fichero línea a línea en bash

```bash
#!/bin/bash

# Verificar si se proporciona un archivo como argumento
if [ $# -ne 1 ]; then
  echo "Uso: $0 <nombre_del_archivo>"
  exit 1
fi

archivo="$1"

# Verificar si el archivo existe
if [ ! -f "$archivo" ]; then
  echo "El archivo $archivo no existe."
  exit 1
fi

# Leer el archivo línea por línea
while IFS= read -r linea; do
  echo "Línea leída: $linea"
done < "$archivo"
```

## 26

Crea un archivo llamado "archivo-secreto.txt" en el home.

Verifica los permisos del archivo utilizando ls -l.

Permite que todos lo puedan leer, cambia de usuario y verifica que otros usuarios lo leen.

Vuelve a tu usuario.

Cambia los permisos del archivo para que solo el propietario tenga permiso de lectura y escritura.

Intenta acceder al archivo como un usuario diferente para comprobar que los permisos se aplican correctamente.
