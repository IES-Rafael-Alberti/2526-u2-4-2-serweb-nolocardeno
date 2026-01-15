# DESPLIEGUE — Evidencias y respuestas

Este documento recopila todas las evidencias y respuestas de la practica.

---

## Parte 1 — Evidencias minimas

### Fase 1: Instalacion y configuracion

1) Servicio Nginx activo

He levantado el contenedor de Nginx con docker compose y he verificado que está corriendo correctamente.

- Que demuestra: El contenedor de Nginx está corriendo y activo
- Comando: `docker compose ps` o `docker ps`
- Evidencia:
  ![Requisito 1](evidencias/requisito1.png)

2) Configuracion cargada

He ejecutado el test de configuración de Nginx para comprobar que no hay errores de sintaxis en el archivo default.conf.

- Que demuestra: La configuración de Nginx se ha cargado correctamente sin errores de sintaxis
- Comando: `docker compose exec web nginx -t`
- Evidencia:
  ![Requisito 2](evidencias/requisito2.png)

3) Resolucion de nombres

He accedido desde el navegador usando localhost y también verificando que se resuelve el nombre configurado (paginaDeNolo) y el puerto configurado para verificar que el servidor responde.

- Que demuestra: El navegador resuelve correctamente el nombre de dominio configurado (paginaDeNolo)
- Evidencia:
  ![Requisito 3](evidencias/requisito3.png)

4) Contenido Web

He subido el contenido web mediante SFTP y he verificado que se muestra correctamente en el navegador.

- Que demuestra: El sitio web se visualiza correctamente en el navegador
- Evidencia:
  ![Requisito 4](evidencias/requisito4.png)

### Fase 2: Transferencia SFTP (Filezilla)

5) Conexion SFTP exitosa

He configurado FileZilla con los datos de conexión (localhost, puerto 2222, usuario y contraseña) y me he conectado al servidor SFTP.

- Que demuestra: Conexión exitosa al servidor SFTP mediante Filezilla
- Evidencia:
  ![Requisito 5](evidencias/requisito5.png)

6) Permisos de escritura

He subido archivos desde FileZilla al servidor SFTP y he comprobado que se guardan correctamente en el volumen compartido.

- Que demuestra: Se pueden subir archivos al servidor SFTP y se reflejan en el volumen compartido
- Evidencia:
  ![Requisito 6](evidencias/requisito6.png)

### Fase 3: Infraestructura Docker

7) Contenedores activos

He verificado que los dos contenedores del docker-compose (web y sftp) están corriendo sin problemas.

- Que demuestra: Los dos contenedores (Nginx y SFTP) están ejecutándose correctamente
- Comando: `docker compose ps` o `docker ps`
- Evidencia:
  ![Requisito 7](evidencias/requisito7.png)

8) Persistencia (Volumen compartido)

He comprobado que los archivos subidos por SFTP son accesibles desde el contenedor de Nginx gracias al volumen compartido.

- Que demuestra: El volumen compartido funciona correctamente entre ambos contenedores
- Evidencia:
  ![Requisito 8](evidencias/requisito8.png)

9) Despliegue multi-sitio

He configurado Nginx para servir el sitio principal en la raíz y otro sitio en la ruta /reloj, y he verificado que ambos funcionan.

- Que demuestra: El servidor Nginx sirve múltiples sitios (root y /reloj)
- Evidencia:
  ![Requisito 9](evidencias/requisito9.png)

### Fase 4: Seguridad HTTPS

10) Cifrado SSL

He generado un certificado autofirmado y lo he configurado en Nginx para habilitar HTTPS en el puerto 8443.

- Que demuestra: El sitio funciona correctamente con HTTPS usando certificado autofirmado
- Evidencia:
  ![Requisito 10](evidencias/requisito10.png)

11) Redireccion forzada

He configurado Nginx para redirigir automáticamente todas las peticiones HTTP a HTTPS y he verificado que devuelve un código 301.

- Que demuestra: Las peticiones HTTP son redirigidas automáticamente a HTTPS (código 301)
- Evidencia:
  ![Requisito 11](evidencias/requisito11.png)

---

## Parte 2 — Evaluacion RA2 (a–j)

### a) Parametros de administracion
- Respuesta:
- Evidencias:
  - evidencias/a-01-grep-nginxconf.png
  - evidencias/a-02-nginx-t.png
  - evidencias/a-03-reload.png

### b) Ampliacion de funcionalidad + modulo investigado
- Opcion elegida (B1 o B2):
- Respuesta:
- Evidencias (B1 o B2):
  - evidencias/b1-01-gzipconf.png
  - evidencias/b1-02-compose-volume-gzip.png
  - evidencias/b1-03-nginx-t.png
  - evidencias/b1-04-curl-gzip.png
  - evidencias/b2-01-defaultconf-headers.png
  - evidencias/b2-02-nginx-t.png
  - evidencias/b2-03-curl-https-headers.png

#### Modulo investigado: <NOMBRE>
- Para que sirve:
- Como se instala/carga:
- Fuente(s):

### c) Sitios virtuales / multi-sitio
- Respuesta:
- Evidencias:
  - evidencias/c-01-root.png
  - evidencias/c-02-reloj.png
  - evidencias/c-03-defaultconf-inside.png

### d) Autenticacion y control de acceso
- Respuesta:
- Evidencias:
  - evidencias/d-01-admin-html.png
  - evidencias/d-02-defaultconf-auth.png
  - evidencias/d-03-curl-401.png
  - evidencias/d-04-curl-200.png

### e) Certificados digitales
- Respuesta:
- Evidencias:
  - evidencias/e-01-ls-certs.png
  - evidencias/e-02-compose-certs.png
  - evidencias/e-03-defaultconf-ssl.png

### f) Comunicaciones seguras
- Respuesta:
- Evidencias:
  - evidencias/f-01-https.png
  - evidencias/f-02-301-network.png

### g) Documentacion
- Respuesta:
- Evidencias: enlaces a todas las capturas

### h) Ajustes para implantacion de apps
- Respuesta:
- Evidencias:
  - evidencias/h-01-root.png
  - evidencias/h-02-reloj.png

### i) Virtualizacion en despliegue
- Respuesta:
- Evidencias:
  - evidencias/i-01-compose-ps.png

### j) Logs: monitorizacion y analisis
- Respuesta:
- Evidencias:
  - evidencias/j-01-logs-follow.png
  - evidencias/j-02-metricas.png

---

## Checklist final

### Parte 1
- [ ] 1) Servicio Nginx activo
- [ ] 2) Configuracion cargada
- [ ] 3) Resolucion de nombres
- [ ] 4) Contenido Web (Cloud Academy)
- [ ] 5) Conexion SFTP exitosa
- [ ] 6) Permisos de escritura
- [ ] 7) Contenedores activos
- [ ] 8) Persistencia (Volumen compartido)
- [ ] 9) Despliegue multi-sitio (/reloj)
- [ ] 10) Cifrado SSL
- [ ] 11) Redireccion forzada (301)

### Parte 2 (RA2)
- [ ] a) Parametros de administracion
- [ ] b) Ampliacion de funcionalidad + modulo investigado
- [ ] c) Sitios virtuales / multi-sitio
- [ ] d) Autenticacion y control de acceso
- [ ] e) Certificados digitales
- [ ] f) Comunicaciones seguras
- [ ] g) Documentacion
- [ ] h) Ajustes para implantacion de apps
- [ ] i) Virtualizacion en despliegue
- [ ] j) Logs: monitorizacion y analisis
