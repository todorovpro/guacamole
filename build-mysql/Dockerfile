ARG GUACAMOLE_VERSION
ARG MYSQL_VERSION

FROM guacamole/guacamole:${GUACAMOLE_VERSION} AS builder
USER root
RUN mkdir -p /opt/guacamole/initdb-mysql
RUN /opt/guacamole/bin/initdb.sh --mysql > /opt/guacamole/initdb-mysql/initdb.sql

FROM mysql:${MYSQL_VERSION}
COPY --from=builder /opt/guacamole/initdb-mysql/initdb.sql /docker-entrypoint-initdb.d/initdb.sql