FROM alpine:latest
MAINTAINER Marcus Andrade "boogermann@tinyretrolabs.org"
ARG BUILD_VERSION

# Core Developement Packages
RUN apk add --update ca-certificates bash git openssh python3 python3-dev && \
    pip3 install --upgrade pip && pip install mkdocs==${BUILD_VERSION} && \
    rm -rf /tmp/* /var/tmp/* /var/cache/apk/* /var/cache/distfiles/*

# Install MKDocs, Extensions and extra themes
RUN pip install mkdocs markdown-include pymdown-extensions pygments lunr nltk six \
	mkdocs-material mkdocs-bootstrap4 mkdocs-gitbook mkdocs-rtd-dropdown

# Set Volume and Workdir
VOLUME /docs
WORKDIR /docs

# Metadata
ARG BUILD_DATE
ARG VCS_REF
LABEL \
	org.label-schema.schema-version="1.0" \
	org.label-schema.vendor="tinyretrolabs.org" \
	org.label-schema.name="tinyretrolabs/mkdocs" \
	org.label-schema.description="Documentation Tool" \
	org.label-schema.url="https://github.com/tinyretrolabs/mkdocs" \
	org.label-schema.vcs-url="https://github.com/tinyretrolabs/mkdocs.git" \
	org.label-schema.build-date=$BUILD_DATE \
	org.label-schema.vcs-ref=$VCS_REF \
	org.label-schema.version=$BUILD_VERSION \
	org.label-schema.docker.cmd="docker run -it --rm -p 8000:8000 -v ${pwd}:/docs tinyretrolabs/mkdocs"

# Set the entry point
ENTRYPOINT ["mkdocs"]

# Use serve as default command
CMD ["serve", "--dev-addr=0.0.0.0:8000"]
