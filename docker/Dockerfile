FROM python:3.13-slim-trixie

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PIP_NO_CACHE_DIR=1

RUN pip install --upgrade pip
RUN apt-get update && apt-get install -y git

COPY ./requirements.txt /
RUN pip install -r requirements.txt

RUN mkdir -p /notebooks /root/.jupyter
COPY jupyter_server_config.py /root/.jupyter/

WORKDIR /notebooks

EXPOSE 8888

CMD ["jupyter", "lab"]
