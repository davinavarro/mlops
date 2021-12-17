# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
FROM $BASE_IMAGE


SHELL ["/bin/bash", "-o", "pipefail", "-c"]

USER root
RUN git clone https://github.com/apache/iceberg.git && \
    cd iceberg/python && \
    pip install -e .

USER ${NB_UID}

ARG DELTA_CORE_VERSION="1.0.0"
RUN pip install --quiet --no-cache-dir delta-spark==${DELTA_CORE_VERSION} && \
     fix-permissions "${HOME}" && \
     fix-permissions "${CONDA_DIR}"

USER root

RUN echo 'spark.sql.extensions io.delta.sql.DeltaSparkSessionExtension' >> "${SPARK_HOME}/conf/spark-defaults.conf" && \
    echo 'spark.sql.catalog.spark_catalog org.apache.spark.sql.delta.catalog.DeltaCatalog' >> "${SPARK_HOME}/conf/spark-defaults.conf"

USER ${NB_UID}