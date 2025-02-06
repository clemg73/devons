FROM python:3.9-slim

WORKDIR /app

COPY ./inventories .
COPY ./roles .
COPY ./launch.yml .

RUN apt-get update && apt-get install -y \
    gcc \
    libffi-dev \
    python3-dev \
    && rm -rf /var/lib/apt/lists/*  # Nettoyer pour réduire la taille de l'image

RUN pip install --no-cache-dir ansible

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh

CMD ["bash", "-c", "echo \"$ID_RSA\" > /root/.ssh/id_rsa && chmod 600 /root/.ssh/id_rsa && cat /root/.ssh/id_rsa"]
