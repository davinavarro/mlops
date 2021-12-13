# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
FROM $BASE_IMAGE

USER root

# RSpark config
ENV R_LIBS_USER "${SPARK_HOME}/R/lib"
RUN fix-permissions "${R_LIBS_USER}"

# R pre-requisites
RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends \
    fonts-dejavu \
    gfortran \
    gcc && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

USER ${NB_UID}

# R packages including IRKernel which gets installed globally.
RUN mamba install --quiet --yes \
    'r-base' \
    'r-ggplot2' \
    'r-irkernel' \
    'r-rcurl' \
    'r-sparklyr' && \
    mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

USER root

RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends \
    gdebi-core
    apt-get clean && rm -rf /var/lib/apt/lists/*
RUN wget https://download2.rstudio.org/server/bionic/amd64/rstudio-server-2021.09.1-372-amd64.deb
RUN gdebi rstudio-server-2021.09.1-372-amd64.deb
USER ${NB_UID}
