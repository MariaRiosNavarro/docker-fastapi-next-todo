FROM python:3.9-alpine

WORKDIR /app

COPY requirements.txt .
RUN apk add --no-cache postgresql-dev gcc python3-dev musl-dev && \
    pip install --no-cache-dir -r requirements.txt

COPY . .


RUN echo '#!/bin/sh' > start.sh && \
    echo 'uvicorn main:app --host 0.0.0.0 --port $PORT --workers 4' >> start.sh && \
    chmod +x start.sh


CMD ["./start.sh"]