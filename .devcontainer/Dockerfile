# Imagem base Alpine com Node.js LTS
FROM node:20-alpine

# Instalação de pacotes essenciais de sistema e desenvolvimento para ambiente Alpine
RUN apk update && apk add --no-cache \
    bash \
    curl \
    git \
    openssh-client \
    sudo \
    shadow \
    tzdata \
    ca-certificates \
    dumb-init

# Garante permissão de sudo sem senha para o usuário não-root 'node' (já existente na imagem node-alpine com UID 1000)
RUN echo "node ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/node \
    && chmod 0440 /etc/sudoers.d/node

# Configura bash como shell padrão para o usuário node
RUN chsh -s /bin/bash node

# Define o diretório de trabalho padrão
WORKDIR /workspace

# Define usuário não-root para execução
USER node

# Configuração global de git para evitar avisos de safe.directory dentro do container
RUN git config --global --add safe.directory /workspace
