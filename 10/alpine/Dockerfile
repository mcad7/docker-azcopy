FROM --platform=linux/amd64 alpine:3.16

ARG RELEASE="20220721"
ARG VERSION="10.16.0"
ARG USER=az
ARG HOMEDIR=/home/${USER}

WORKDIR /tmp

RUN apk --update add libc6-compat jq
RUN wget https://azcopyvnext.azureedge.net/release${RELEASE}/azcopy_linux_amd64_${VERSION}.tar.gz

RUN tar xf azcopy_linux_amd64_${VERSION}.tar.gz && \
    chmod +x azcopy_linux_amd64_${VERSION}/azcopy && \
    mv azcopy_linux_amd64_${VERSION}/azcopy /usr/local/bin/azcopy && \
    rm -rf azcopy_linux_amd64_* /var/cache/apk/*

RUN adduser --uid 666 --shell /bin/sh -D --home ${HOMEDIR} ${USER}

WORKDIR ${HOMEDIR}
USER ${USER}

ENTRYPOINT [ "azcopy" ]

CMD [ "--help" ]