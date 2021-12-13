FROM $BASE_IMAGE

USER root
RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y --no-install-recommends \
        dnsutils \
        git \
        iputils-ping \
 && rm -rf /var/lib/apt/lists/*
USER $NB_USER

COPY requirements.txt /tmp/requirements.txt
RUN python -m pip install --no-cache-dir \
    -r /tmp/requirements.txt

# Support overriding a package or two through passed docker --build-args.
# ARG PIP_OVERRIDES="jupyterhub==1.3.0"
ARG PIP_OVERRIDES=
RUN if [[ -n "$PIP_OVERRIDES" ]]; then \
        pip install --no-cache-dir $PIP_OVERRIDES; \
    fi

RUN jupyter serverextension enable --py nbgitpuller --sys-prefix

# Uncomment the line below to make nbgitpuller default to start up in JupyterLab
ENV NBGITPULLER_APP=lab
ENV JUPYTER_ENABLE_LAB=yes
# conda/pip/apt install additional packages here, if desired.