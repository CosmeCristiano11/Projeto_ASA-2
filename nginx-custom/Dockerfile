FROM nginx:latest

# Instalar ping e curl
RUN apt-get update && \
    apt-get install -y --no-install-recommends iputils-ping curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Copiar configuração do nginx para proxy reverso
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 8080
