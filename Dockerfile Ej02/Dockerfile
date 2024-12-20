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
	apt-get install -y nano proftpd openssl proftpd-mod-crypto

# Copiamos todos los ficheros que necesitamos

COPY 	proftpd.crt /etc/ssl/certs
COPY 	proftpd.key /etc/ssl/private

COPY 	proftpd.conf /etc/proftpd/proftpd.conf
COPY 	tls.conf /etc/proftpd/tls.conf
COPY 	modules.conf /etc/proftpd/modules.conf


RUN useradd -d /srv/deaw -s /sbin/nologin deaw && \
	echo "deaw:deaw" | chpasswd && \
	mkdir /srv/deaw  && \
	chown -R deaw:deaw /srv/deaw && \
	chmod -R 766 /srv/deaw


# Copiamos los recursos facilitados en la tarea
COPY 	Recursos2/. /srv/deaw/

RUN service proftpd restart 

# Indica los puertos que utiliza la imagen
# para que los mapeemos al crear el contenedor
EXPOSE 21

# Comando por defecto para ejecutar cuando se inicie el contenedor
CMD ["proftpd", "--nodaemon"]