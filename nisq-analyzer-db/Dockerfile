FROM postgres

# copy db dump (https://github.com/UST-QuAntiL/nisq-analyzer-content/blob/master/prioritization-based-on-learned-weights/sample-data/20220313_nisq.sql)
COPY nisq.sql /docker-entrypoint-initdb.d/

EXPOSE 5060

CMD su postgres -c "/usr/local/bin/docker-entrypoint.sh postgres -p 5060"