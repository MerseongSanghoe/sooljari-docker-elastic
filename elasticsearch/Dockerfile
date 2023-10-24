ARG ELASTIC_VERSION

# https://www.docker.elastic.co/
FROM docker.elastic.co/elasticsearch/elasticsearch:${ELASTIC_VERSION}

# Add your elasticsearch plugins setup here
# Example: RUN elasticsearch-plugin install analysis-icu
RUN elasticsearch-plugin install analysis-nori
RUN elasticsearch-plugin install https://github.com/netcrazy/elasticsearch-jaso-analyzer/releases/download/v8.6.2/jaso-analyzer-plugin-8.6.2-plugin.zip
