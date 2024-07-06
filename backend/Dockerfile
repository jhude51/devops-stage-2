FROM python:3.12-slim

WORKDIR /app/

RUN apt-get update && apt-get install -y curl && \ 
    curl -sSL https://install.python-poetry.org | POETRY_HOME=/opt/poetry python3 && \
    cd /usr/local/bin && \
    ln -s /opt/poetry/bin/poetry && \
    poetry config virtualenvs.create false

COPY ./pyproject.toml ./poetry.lock* /app/

RUN poetry install --no-root --no-interaction --no-ansi

COPY ./prestart.sh /app/

COPY ./alembic.ini /app/

COPY ./app /app/

CMD ["uvicorn", "app.main:app", "--reload"]
