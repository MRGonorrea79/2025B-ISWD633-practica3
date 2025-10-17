# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.

# Reflexión sobre Volúmenes y Mounts en Docker

Antes de la práctica, tenía un conocimiento general de que los contenedores podían almacenar datos, pero no comprendía completamente las diferencias entre volúmenes, bind mounts y volúmenes nombrados, ni los problemas que podían surgir al gestionarlos.

Durante la práctica, aprendí lo siguiente:

- Los volúmenes en Docker permiten persistir datos más allá del ciclo de vida del contenedor. Los volúmenes pueden ser anónimos (creados automaticamente por Docker) o nombrados (gestionados por el usuario, lo que facilita la reutilización y el respaldo de datos).

- Los bind mounts permiten mapear directorios o archivos específicos del host dentro del contenedor. Son útiles para desarrollo, porque se reflejan cambios inmediatamente, pero pueden generar problemas si la ruta del host no existe, si hay errores de permisos o si la ruta contiene caracteres no válidos.  

- Durante la práctica, me encontré con un problema: al usar bind mounts con rutas mal definidas o relativas (`${PWD}/ en Windows por ejemplo), Docker no reconocía el path y fallaba al crear el contenedor.

- Otro punto importante que observé es que, al montar un bind, los archivos que ya existían en el contenedor pueden "desaparecer" temporalmente, porque el directorio del host sobrescribe el contenido del contenedor en ese punto de montaje. Esto requiere precaución al preparar contenedores que ya tengan datos importantes por defecto.

Las principales diferencias que note fueron:
  - Volúmenes nombrados: mejor para producción y persistencia segura de datos.  
  - Bind mounts: útiles para desarrollo y pruebas, pero requieren cuidado con rutas y permisos.  


