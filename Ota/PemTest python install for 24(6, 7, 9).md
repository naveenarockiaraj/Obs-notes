we cant able to install directly in the file so we use to build as docker with the decencies
by these changes
- have to manually added the python library version in ==pipfile==
	- `filetype = "^1.2.0"`change these into below one
	- `filetype = "==1.2.0"`
- and made change in ==dockerfile==
	- after these changes take bulid in the repo
	- because that will help to install the package
- after the build have completed enter this code in terminal
	- git checkout  Dockerfile
	- `mv ~/Downloads/Pipfile.lock Pipfile.lock
	- and again take the build 
	  and again up the compose
24.06 `
```
	- #IoTium OTAccess APIGateway dockerfile

#Author: Sandeep Machiraju

#Maintainer: IoTium

#Date: 08/21/2018

FROM python:3.9.18-slim-bullseye@sha256:c373b27f219903d080b4023da5727ae2cdaeb1632026e95b8814b80bd52d3cd5 as builder

  

ENV PIPENV_VENV_IN_PROJECT=True

  

WORKDIR /

  

COPY Pipfile Pipfile

# COPY Pipfile.lock Pipfile.lock

  

#Dependencies

RUN apt-get update && apt-get clean && apt-get install -y --no-install-recommends \

    build-essential \

    apt-utils \

    curl \

    libldap2-dev \

    libsasl2-dev \

    ldap-utils \

    libssl-dev \

    librdkafka-dev \

    samba-common-bin \

    samba-dsdb-modules \

    && rm -rf /var/lib/apt/lists/*

  

RUN python3 -m pip install pipenv==2022.4.30 \

  && python3 -m pipenv install \

  && python3 -m pipenv requirements > /tmp/requirements.txt

  

#Base Image

FROM python:3.9.18-slim-bullseye@sha256:c373b27f219903d080b4023da5727ae2cdaeb1632026e95b8814b80bd52d3cd5

  

LABEL maintainer="ioTium OTA Engg <otaeng@iotium.io>"

  

ARG GIT_COMMIT=""

ENV DEBIAN_FRONTEND=noninteractive

#---------------#

# Installation  #

#---------------#

#Dependencies

RUN apt-get update && apt-get clean && apt-get install -y --no-install-recommends \

    build-essential \

    apt-utils \

    curl \

    libldap2-dev \

    libsasl2-dev \

    ldap-utils \

    libssl-dev \

    librdkafka-dev \

    samba-common-bin \

    samba-dsdb-modules \

    && rm -rf /var/lib/apt/lists/*

  

COPY --from=builder /tmp/requirements.txt /tmp/requirements.txt

COPY --from=builder Pipfile.lock /tmp/Pipfile.lock

  

RUN python3 -m pip install --no-cache-dir -r /tmp/requirements.txt

  

WORKDIR /apigateway

#Copy the api binary files (Core Files)

# Maxmind db as separate layer to speedup the build.

COPY janusviewer/GeoLite2-City.mmdb .

COPY janusviewer/*.py ./

COPY gunicorn_config.py .

COPY janusviewer/api ./api

  

ARG GIT_COMMIT=unspecified

ARG BUILD_IMAGE_ID=unspecified

ENV GIT_COMMIT=${GIT_COMMIT}

ENV BUILD_IMAGE_ID=${BUILD_IMAGE_ID}

  

#Set the PYTHONPATH env variable [Must]

ENV PYTHONPATH=/apigateway:/usr/lib/python3/dist-packages

ENV APPLICATIONPATH=/apigateway

ENV OTA_API_SETUP=production

ENV OTA_APIGW_PORT=5000

ENV OTA_APIGW_WORKERS=4

ENV TZ UTC

VOLUME [ "/apigateway/logs", "/apigateway/logs/gunicorn" ]

  

#Run the Gunicorn Appl. Server

CMD gunicorn -c gunicorn_config.py startjanus:application

#--certfile /apigateway/apicerts/cert.pem --keyfile /apigateway/apicerts/key.pem startjanus:application

#CMD cd /apigateway && gunicorn -c /apigateway/gunicorn_config.py --log-file=- startjanus:application
```
24.07
```
# IoTium OTAccess APIGateway dockerfile

# Maintainer: IoTium

# Date: 20/07/2024

FROM python:3.11.9-slim-bookworm@sha256:80bcf8d243a0d763a7759d6b99e5bf89af1869135546698be4bf7ff6c3f98a59 as builder

  

ENV PIPENV_VENV_IN_PROJECT=True

  

WORKDIR /

  

COPY Pipfile Pipfile

# COPY Pipfile.lock Pipfile.lock

  

# Dependencies

RUN apt-get update && apt-get clean && apt-get install -y libc6 && apt-get install -y --no-install-recommends \

    build-essential \

    apt-utils \

    libldap2-dev \

    libsasl2-dev \

    ldap-utils \

    libssl-dev \

    libffi-dev \

    python3.11-dev \

    samba-common-bin \

    samba-dsdb-modules \

    && rm -rf /var/lib/apt/lists/*

  

RUN python3 -m pip install pipenv==2022.4.30 \

  && python3 -m pipenv install \

  && python3 -m pipenv requirements > /tmp/requirements.txt

  

# Base Image

FROM python:3.11.9-slim-bookworm@sha256:80bcf8d243a0d763a7759d6b99e5bf89af1869135546698be4bf7ff6c3f98a59 as build-env

  

LABEL maintainer="ioTium OTA Engg <otaeng@iotium.io>"

  

ARG GIT_COMMIT=""

ENV DEBIAN_FRONTEND=noninteractive

  

# Dependencies

RUN apt-get update && apt-get clean && apt-get install -y libc6 && apt-get install -y --no-install-recommends \

    build-essential \

    apt-utils \

    libldap2-dev \

    libsasl2-dev \

    ldap-utils \

    libssl-dev \

    libffi-dev \

    python3.11-dev \

    samba-common-bin \

    samba-dsdb-modules \

    && rm -rf /var/lib/apt/lists/*

  

COPY --from=builder /tmp/requirements.txt /tmp/requirements.txt

COPY --from=builder Pipfile.lock /tmp/Pipfile.lock

  

RUN python3 -m pip install --target=/apigateway --no-cache-dir -r /tmp/requirements.txt

  

WORKDIR /apigateway

# Copy the api binary files (Core Files)

# Maxmind db as separate layer to speedup the build.

COPY janusviewer/GeoLite2-City.mmdb .

COPY janusviewer/*.py ./

COPY gunicorn_config.py .

COPY healthcheck.py .

COPY janusviewer/api ./api

  

FROM gcr.io/distroless/python3-debian12@sha256:078ef2498f450dddbabf7c46f889016824c8c032f84edd2017cd135a2b4bae91

COPY --from=build-env /apigateway /apigateway

COPY --from=build-env /usr/bin/ldap* /usr/bin/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libldap* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/liblber* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libsasl* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/sasl2/libsasl* /usr/lib/x86_64-linux-gnu/sasl2/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/pkgconfig/libsasl2.pc /usr/lib/x86_64-linux-gnu/pkgconfig/libsasl2.pc

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libgnutls* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libp11-kit* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libidn2* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libunistring* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libtasn1* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libnettle* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libhogweed* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libgmp* /usr/lib/x86_64-linux-gnu/

  
  

COPY --from=build-env /usr/share/samba /usr/share/samba

COPY --from=build-env /usr/sbin/samba_kcc /usr/sbin/samba_kcc

COPY --from=build-env /usr/bin/samba-tool /usr/bin/samba-tool

COPY --from=build-env /usr/bin/samba-regedit /usr/bin/samba-regedit

  

COPY --from=build-env /run/samba /run/samba

COPY --from=build-env /etc/samba /etc/samba

COPY --from=build-env /var/lib/samba /var/lib/samba

COPY --from=build-env /var/log/samba /var/log/samba

COPY --from=build-env /var/cache/samba /var/cache/samba

COPY --from=build-env /usr/lib/x86_64-linux-gnu/samba /usr/lib/x86_64-linux-gnu/samba

COPY --from=build-env /usr/lib/python3/dist-packages/samba /usr/lib/python3.11/dist-packages/samba

COPY --from=build-env /usr/lib/python3/dist-packages/ldb* /usr/lib/python3.11/dist-packages/

COPY --from=build-env /usr/lib/python3/dist-packages/talloc* /usr/lib/python3.11/dist-packages/

COPY --from=build-env /usr/lib/python3/dist-packages/tdb* /usr/lib/python3.11/dist-packages/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/ldb /usr/lib/x86_64-linux-gnu/ldb

COPY --from=build-env /usr/lib/x86_64-linux-gnu/libldb* /usr/lib/x86_64-linux-gnu/

COPY --from=build-env /usr/include/x86_64-linux-gnu/bits/*ldb* /usr/include/x86_64-linux-gnu/bits/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/sasl2/*ldb* /usr/lib/x86_64-linux-gnu/sasl2/

COPY --from=build-env /usr/lib/python3/dist-packages/_ldb_text.py /usr/lib/python3/dist-packages/_ldb_text.py

  

COPY --from=build-env /lib/x86_64-linux-gnu/*.so* /lib/x86_64-linux-gnu/

COPY --from=build-env /usr/lib/x86_64-linux-gnu/*.so* /usr/lib/x86_64-linux-gnu/

  

COPY --from=build-env /tmp/Pipfile.lock /tmp/Pipfile.lock

  
  

WORKDIR /apigateway

  

ARG GIT_COMMIT=unspecified

ARG BUILD_IMAGE_ID=unspecified

ENV GIT_COMMIT=${GIT_COMMIT}

ENV BUILD_IMAGE_ID=${BUILD_IMAGE_ID}

  

# Set the PYTHONPATH env variable [Must]

ENV PYTHONPATH=/apigateway:/usr/lib/python3.11/dist-packages/

ENV APPLICATIONPATH=/apigateway

ENV OTA_API_SETUP=production

ENV OTA_APIGW_PORT=5000

ENV OTA_APIGW_WORKERS=4

ENV TZ UTC

VOLUME [ "/apigateway/logs", "/apigateway/logs/gunicorn" ]

  

# Run the Gunicorn Appl. Server

CMD ["/apigateway/bin/gunicorn", "-c", "/apigateway/gunicorn_config.py", "startjanus:application"]
```
