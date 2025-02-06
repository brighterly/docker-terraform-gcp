FROM alpine:3.17

RUN apk add --no-cache \
      bash \
      curl \
      unzip \
      python3 \
      py3-pip \
      py3-crcmod

ENV TERRAFORM_VERSION=1.9.8

RUN curl -fsSL https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -o terraform.zip \
    && unzip terraform.zip \
    && mv terraform /usr/local/bin/ \
    && rm terraform.zip

ENV GLIBC_VERSION="2.35-r1"
RUN apk add --no-cache --virtual=.build-deps ca-certificates wget \
    && wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
    && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}/glibc-${GLIBC_VERSION}.apk \
    && apk add glibc-${GLIBC_VERSION}.apk \
    && rm glibc-${GLIBC_VERSION}.apk \
    && apk del .build-deps

ENV GCLOUD_SDK_VERSION=509.0.0
RUN curl -fsSL "https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-${GCLOUD_SDK_VERSION}-linux-x86_64.tar.gz" -o gcloud.tar.gz \
    && tar -xzf gcloud.tar.gz \
    && rm gcloud.tar.gz \
    && ./google-cloud-sdk/install.sh --quiet

ENV PATH="/google-cloud-sdk/bin:/usr/local/bin:${PATH}"
