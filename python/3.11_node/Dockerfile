FROM python:3.11-slim

LABEL author="HoggyTheWizard" maintainer="hoggydev@proton.me"

RUN apt-get update \
    && apt-get install -y git gcc g++ ca-certificates dnsutils curl iproute2 ffmpeg procps \
    && useradd -m -d /home/container container

# Install Node.js and npm
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - \
    && apt-get install -y nodejs

# Update npm to the latest version
RUN npm install -g npm@latest

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
