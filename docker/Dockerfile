FROM python:3.13-slim-trixie

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PIP_NO_CACHE_DIR=1

RUN pip install --upgrade pip
RUN apt-get update && apt-get install -y git

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        r-base \
        r-base-dev \
        libcurl4-openssl-dev \
        libssl-dev \
        libxml2-dev \
        xtail \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install radian (modern R console) and httpgd (for fast HTML plot viewing) via pip
# Assumes python3 and pip are already installed in your AI base image
RUN pip3 install --no-cache-dir radian
RUN R -e "install.packages(c('httpgd', 'languageserver'), repos='https://r-project.org')"


COPY ./requirements.txt /
RUN pip install -r requirements.txt

RUN mkdir -p /notebooks /root/.jupyter
COPY jupyter_server_config.py /root/.jupyter/

WORKDIR /notebooks

EXPOSE 8888

CMD ["jupyter", "lab"]
