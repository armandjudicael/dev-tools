FROM python:3.11-slim

WORKDIR /app
COPY . .
RUN pip install -r requirements.txt

ENTRYPOINT ["functions-framework"]
CMD ["--target=hello_world", "--port=8082"]
