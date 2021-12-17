FROM datamechanics/spark:3.2.0-latest


RUN wget -q https://repo1.maven.org/maven2/io/delta/delta-core_2.12/1.1.0/delta-core_2.12-1.1.0.jar
RUN cp delta-core_2.12-1.1.0.jar /opt/spark/jars/delta-core_2.12-1.1.0.jar


RUN wget -q https://repo1.maven.org/maven2/org/apache/iceberg/iceberg-spark3-runtime/0.12.1/iceberg-spark3-runtime-0.12.1.jar
RUN cp iceberg-spark3-runtime-0.12.1.jar /opt/spark/jars/iceberg-spark3-runtime-0.12.1.jar


RUN rm iceberg-spark3-runtime-0.12.1.jar delta-core_2.12-1.1.0.jar
