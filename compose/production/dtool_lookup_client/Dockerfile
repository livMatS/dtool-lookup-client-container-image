FROM python:3.9.7-slim

ENV PYTHONUNBUFFERED 1

RUN mkdir -p /root/.config/dtool
COPY dtool/dtool.json /root/.config/dtool

RUN apt-get --yes update && \
    apt-get --no-install-recommends --yes install git smbclient && \
    rm -rf /var/lib/apt/lists/*

COPY compose/production/dtool_lookup_client/requirements.txt /requirements.txt
RUN pip install --no-cache-dir -r /requirements.txt

ENTRYPOINT ["/usr/local/bin/dtool"]
CMD ["--help"]
