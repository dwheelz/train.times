FROM python:3.10.5-slim-bullseye

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install tzdata -y \
    && pip3 install --upgrade pip pip-tools

# INSTALL REQUIREMENTS
COPY requirements.txt /
RUN pip-sync requirements.txt
RUN rm requirements.txt

# CREATE APP DIR
RUN mkdir app

# MAKE TRAINUSER
RUN groupadd -r trainuser && useradd -rm -d /home/trainuser -s /bin/bash -g  trainuser trainuser
USER trainuser

WORKDIR /app
