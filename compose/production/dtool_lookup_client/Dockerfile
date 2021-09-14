FROM python:3.9.7-slim

ENV PYTHONUNBUFFERED 1

RUN mkdir /app
RUN mkdir -p /root/.config/dtool

COPY tests/dtool /share/dtool
COPY dtool/dtool.json /root/.config/dtool

COPY compose/production/dtool_lookup_client/start /start

RUN sed -i 's/\r//' /start
RUN chmod +x /start

RUN apt-get --yes update && \
    apt-get --no-install-recommends --yes install git smbclient && \
    rm -rf /var/lib/apt/lists/*

COPY compose/production/dtool_lookup_client/requirements.txt /requirements.txt
RUN pip install -r /requirements.txt
