Examen Interciclo
Antes de correr el codigo debemos tener instalado el servidor de angular:
npm install
1. Para construir la img del contenedor debemos ejecutar el comando:
docker build .t exameninterciclov1 .
2. Para correr el contenedor hacia un servicio web (Puerto 80)
docker run -p 8080:80 exameninterciclov1
3. Para ingresar al servicio web, mediante un navegador colocar localhost:80
Luego de ello dar click en "browser" y se direccionara a la pagina principal.
