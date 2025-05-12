FROM docker.n8n.io/n8nio/n8n:latest
USER root
RUN apk add --update --no-cache docker-cli

#RUN apk update && apk add --update docker openrc
#RUN rc-update add docker boot
USER node
# Verificar la instalación
RUN docker --version