FROM jupyter/pyspark-notebook
USER root
RUN apt-get update -y && apt-get install -y alien
RUN wget https://download.dremio.com/odbc-driver/1.4.2.1003/dremio-odbc-1.4.2.1003-1.x86_64.rpm 
RUN alien -i dremio-odbc-1.4.2.1003-1.x86_64.rpm --scripts
RUN apt-get install -y unixodbc-dev
RUN pip install pyodbc && pip install sqlalchemy_dremio && pip install dremio_client[full]
RUN wget -q https://archive.apache.org/dist/spark/spark-3.0.2/spark-3.0.2-bin-hadoop3.2.tgz
RUN tar xf spark-3.0.2-bin-hadoop3.2.tgz
RUN unzip -q /home/jovyan/spark-3.0.2-bin-hadoop3.2/python/lib/py4j-0.10.9-src.zip
RUN pip install pyspark==3.0.2 && pip -q install findspark
USER jupyter