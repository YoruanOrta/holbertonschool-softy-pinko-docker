FROM ubuntu:latest

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y python3 python3-pip && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY ./api.py /app/api.py
COPY ./requirements.txt /app/requirements.txt

RUN pip3 install --no-cache-dir --break-system-packages -r requirements.txt

EXPOSE 5252

CMD ["python3", "api.py"]