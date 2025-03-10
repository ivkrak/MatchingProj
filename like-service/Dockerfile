FROM python:3.12-alpine

RUN apk add --no-cache gcc musl-dev libffi-dev && \
    pip install --no-cache-dir uv

WORKDIR /app

COPY pyproject.toml .
COPY uv.lock .
RUN uv sync

COPY app.py .
COPY config/ ./config
COPY db/ ./db
COPY IPC/ ./IPC
COPY resources/ ./resources

CMD ["faststream", "run", "app:app"]
