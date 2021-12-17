# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
FROM $BASE_IMAGE


SHELL ["/bin/bash", "-o", "pipefail", "-c"]

USER root
RUN git clone https://github.com/apache/iceberg.git && \
    cd iceberg/python && \
    pip install -e . && \

USER ${NB_UID}

# R packages including IRKernel which gets installed globally.
RUN mamba install --quiet --yes \
    'delta-spark' && \
    mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"