FROM datamechanics/spark:3.2.0-latest

USER root

ENV PYSPARK_MAJOR_PYTHON_VERSION=3
WORKDIR /opt/application/

RUN wget  https://repo1.maven.org/maven2/io/delta/delta-core_2.12/1.1.0/delta-core_2.12-1.1.0.jar
RUN mv delta-core_2.12-1.1.0.jar /opt/spark/jars

RUN wget https://repo1.maven.org/maven2/org/apache/iceberg/iceberg-spark3-runtime/0.12.1/iceberg-spark3-runtime-0.12.1.jar
RUN mv iceberg-spark3-runtime-0.12.1.jar /opt/spark/jars