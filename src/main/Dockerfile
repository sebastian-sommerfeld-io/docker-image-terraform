FROM hashicorp/terraform:1.3.9
LABEL maintainer="sebastian@sommerfeld.io"

# Install basics
ARG CURL_VERSION="7.88.1-r0"
RUN apk update \
    && apk --no-cache add curl=${CURL_VERSION} \
    && apk --no-cache add libcurl=${CURL_VERSION} \
    && apk --no-cache add unzip=6.0-r13

# Install Bitwarden CLI + dependencies
ARG BW_VERSION="2022.11.0"
RUN apk --no-cache add libc6-compat=1.2.3-r4 \
    && apk --no-cache add gcompat=1.1.0-r0 \
    && apk --no-cache add libgcc=12.2.1_git20220924-r4 \
    && apk --no-cache add libstdc++=12.2.1_git20220924-r4 \
    && rm -rf /var/cache/apk/* \
    && curl -L https://github.com/bitwarden/clients/releases/download/cli-v${BW_VERSION}/bw-linux-${BW_VERSION}.zip -o bw.zip \
    && unzip bw.zip \
    && chmod +rx bw \
    && rm bw.zip \
    && mv bw /usr/local/bin
