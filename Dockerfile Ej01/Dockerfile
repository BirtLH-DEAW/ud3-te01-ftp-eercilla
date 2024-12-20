# Crea una nueva imagen a partir de Ubuntu, última versión

FROM ubuntu:latest

# Información
LABEL \
	authors="eercilla" \
	version="1.0" \
	description="Ubuntu"

# Ejecutamos diferentes comandos
# Encadenamos en un mismo RUN mediante la \
RUN \
	apt-get update && \
	apt-get upgrade -y && \
	apt-get install -y nano proftpd

# Copiamos todos los ficheros que necesitamos
COPY 	proftpd.conf /etc/proftpd/proftpd.conf

# Copiamos los recursos facilitados en la tarea
COPY 	Recursos1/. /srv/ftp/


# Indica los puertos que utiliza la imagen
# para que los mapeemos al crear el contenedor
EXPOSE 21

# Comando por defecto para ejecutar cuando se inicie el contenedor
CMD ["proftpd", "--nodaemon"]