FROM python:3.9-slim

WORKDIR /app

COPY ./inventories ./inventories
COPY ./roles ./roles
COPY ./launch.yml ./launch.yml

RUN apt-get update && apt-get install -y \
    gcc \
    libffi-dev \
    python3-dev \
    openssh-client

RUN pip install --no-cache-dir ansible

CMD ["bash", "-c", "ansible-playbook -i /app/inventories/setup.yml /app/launch.yml"]
