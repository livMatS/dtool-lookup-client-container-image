FROM python:3.11.2-slim

ENV PYTHONUNBUFFERED 1

RUN mkdir -p /root/.config/dtool
COPY dtool/dtool.json /root/.config/dtool

RUN apt-get --yes update && \
    apt-get --no-install-recommends --yes install git smbclient && \
    rm -rf /var/lib/apt/lists/*

COPY compose/production/dtool/requirements.txt /requirements.txt
RUN pip install --no-cache-dir setuptools_scm
RUN pip install --no-cache-dir -r /requirements.txt

ENTRYPOINT ["/usr/local/bin/dtool"]
CMD ["--help"]
