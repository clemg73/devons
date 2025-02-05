FROM python:3.9-slim

WORKDIR /app

COPY ./inventories .
COPY ./roles .
COPY ./launch.yml .

CMD ["bash", "-c", "sudo ansible-playbook -i /app/inventories/setup.yml /app/launch.yml"]
