FROM opensearchproject/opensearch:1.1.0

ARG ANALYSIS_EXTENSION_PLUGIN=org.codelibs.opensearch:opensearch-analysis-extension:1.1.0
ARG ANALYSIS_FESS_PLUGIN=org.codelibs.opensearch:opensearch-analysis-fess:1.1.0
ARG MINHASH_PLUGIN=org.codelibs.opensearch:opensearch-minhash:1.1.0
ARG CONFIGSYNC_PLUGIN=org.codelibs.opensearch:opensearch-configsync:1.1.0

RUN /usr/share/opensearch/bin/opensearch-plugin install $ANALYSIS_FESS_PLUGIN -b  && \
    /usr/share/opensearch/bin/opensearch-plugin install $ANALYSIS_EXTENSION_PLUGIN -b && \
    /usr/share/opensearch/bin/opensearch-plugin install $MINHASH_PLUGIN -b && \
    /usr/share/opensearch/bin/opensearch-plugin install $CONFIGSYNC_PLUGIN -b && \
    echo 'configsync.config_path: ${FESS_DICTIONARY_PATH}' >> /usr/share/opensearch/config/opensearch.yml && \
    mkdir /usr/share/opensearch/config/dictionary && \
    chown opensearch /usr/share/opensearch/config/dictionary

