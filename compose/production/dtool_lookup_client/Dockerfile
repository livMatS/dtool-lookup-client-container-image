FROM python:3.8-slim

ENV PYTHONUNBUFFERED 1

RUN apt-get --yes update && \
    apt-get --no-install-recommends --yes install git smbclient && \
    rm -rf /var/lib/apt/lists/*

RUN pip install PyYAML dtool dtool-smb dtool-lookup-api git+https://github.com/IMTEK-Simulation/dtool-lookup-client@master
#
# Prepare application code
#
RUN mkdir /app
RUN mkdir -p /root/.config/dtool

COPY tests/dtool /share/dtool
COPY dtool/dtool.json /root/.config/dtool

COPY compose/production/dtool_lookup_client/start /start

RUN sed -i 's/\r//' /start
RUN chmod +x /start
