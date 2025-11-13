FROM python:3.11-slim

WORKDIR /app

COPY . .

RUN chmod +x run.sh

EXPOSE 3000

RUN pip install -r requirements.txt

CMD ["./run.sh"]