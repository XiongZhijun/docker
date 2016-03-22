
FROM kibana:4.4.2

RUN kibana plugin --install elastic/sense \
	&& kibana plugin --install elasticsearch/marvel/latest

EXPOSE 5601
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["kibana"]
