FROM python:3.12-alpine

RUN apk add --no-cache gcc musl-dev libffi-dev && \
    pip install --no-cache-dir uv gunicorn fastapi uvicorn psycopg2-binary

WORKDIR /app

COPY pyproject.toml uv.lock ./
RUN uv venv .venv && uv pip install --system --requirement requirements.txt

COPY app.py .
COPY config/ ./config
COPY db/ ./db
COPY IPC/ ./IPC
COPY resources/ ./resources


CMD ["faststream", "run", "app:app"]
