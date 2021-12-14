FROM python:3.8.12
ARG MLFLOW_VERSION=1.22.0


RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y --no-install-recommends \
        default-libmysqlclient-dev \
        build-essential  \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /mlflow/
COPY requirements.txt /tmp/requirements.txt
RUN python -m pip install --no-cache-dir \
    -r /tmp/requirements.txt
EXPOSE 5000

ENV BACKEND_URI sqlite:////mlflow/mlflow.db
ENV ARTIFACT_ROOT /mlflow/artifacts

CMD mlflow server --backend-store-uri ${BACKEND_URI} --default-artifact-root ${ARTIFACT_ROOT} --host 0.0.0.0 --port 5000