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

RUN mkdir -p /ssh
RUN echo "${ID_RSA}" > /ssh/id_rsa

CMD ["bash", "-c", "ansible-playbook -i /app/inventories/setup.yml /app/launch.yml"]
