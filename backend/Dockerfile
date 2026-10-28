FROM python:3.12.10-alpine3.21

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app

RUN apk update && apk upgrade --no-cache && apk add --no-cache gcc musl-dev postgresql-dev shadow && addgroup -S app && adduser -S -G app app

COPY requirements.txt ./
RUN pip install --upgrade pip && pip install --no-cache-dir -r requirements.txt

COPY app.py ./
RUN chown -R app:app /app

USER app

CMD ["python", "app.py"]
