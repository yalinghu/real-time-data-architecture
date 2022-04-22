FROM preset/superset:latest
USER root
RUN apt-get update -y && apt-get install -y alien
RUN wget https://download.dremio.com/odbc-driver/1.4.2.1003/dremio-odbc-1.4.2.1003-1.x86_64.rpm -P /tmp/
RUN alien -k -i /tmp/dremio-odbc-1.4.2.1003-1.x86_64.rpm --scripts
RUN apt-get install -y unixodbc-bin && apt-get install -y unixodbc-dev
RUN pip install pyodbc && pip install sqlalchemy_dremio && pip install dremio_client[full]
USER superset
RUN superset fab create-admin --username admin --firstname Superset --lastname Admin --email admin@superset.com --password admin
RUN superset db upgrade
RUN superset init

