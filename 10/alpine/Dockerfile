FROM --platform=linux/amd64 alpine:3.16

ARG RELEASE="20221005"
ARG VERSION="10.16.1"
ARG HOMEDIR=/root/

WORKDIR /tmp

RUN apk --update add libc6-compat jq
RUN wget https://azcopyvnext.azureedge.net/release${RELEASE}/azcopy_linux_amd64_${VERSION}.tar.gz

RUN tar xf azcopy_linux_amd64_${VERSION}.tar.gz && \
    chmod +x azcopy_linux_amd64_${VERSION}/azcopy && \
    mv azcopy_linux_amd64_${VERSION}/azcopy /usr/local/bin/azcopy && \
    rm -rf azcopy_linux_amd64_* /var/cache/apk/*

WORKDIR ${HOMEDIR}
ENTRYPOINT [ "azcopy" ]

CMD [ "--help" ]