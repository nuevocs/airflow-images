FROM apache/airflow:2.7.0rc1-python3.11

USER root
ENV PIP_ROOT_USER_ACTION=ignore
RUN mkdir -p /opt/airflow/temp
RUN apt-get update && \
    apt-get install --no-install-recommends -y curl && \
    apt-get clean
RUN apt update && apt install python3 python3-pip -y
RUN apt-get install -y libnss3 libasound2 libgbm-dev


RUN python3 -m pip install playwright
RUN python3 -m playwright install --with-deps

USER airflow
RUN pip install --user --upgrade pip
COPY airflow-playwright/requirements.txt /requirements.txt
RUN pip install --no-cache-dir --user -r /requirements.txt

RUN playwright install