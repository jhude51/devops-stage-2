FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV PYTHONPATH "${PYTHONPATH}:/app"

WORKDIR /app/

RUN apt-get update && apt-get install -y curl && \ 
    curl -sSL https://install.python-poetry.org | POETRY_HOME=/opt/poetry python3 && \
    cd /usr/local/bin && \
    ln -s /opt/poetry/bin/poetry && \
    poetry config virtualenvs.create true

COPY pyproject.toml poetry.lock* /app/

RUN poetry install --no-dev --no-interaction --no-ansi

COPY . /app/

RUN chmod +x /app/prestart.sh

EXPOSE 8000

ENTRYPOINT ["poetry", "run", "bash", "-c", "/app/prestart.sh && uvicorn app.main:app --host 0.0.0.0 --port 8000"]
