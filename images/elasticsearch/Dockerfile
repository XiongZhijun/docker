
FROM kibana:2.2.1

ADD plugins ./plugins

RUN bin/plugin install license \
	&& bin/plugin install marvel-agent \
	&& bin/plugin install mobz/elasticsearch-head

COPY config ./config

VOLUME /usr/share/elasticsearch/data

EXPOSE 9200 9300
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["elasticsearch"]
