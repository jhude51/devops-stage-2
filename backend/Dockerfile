FROM python:3.12.3

WORKDIR /app/

RUN curl -sSL https://install.python-poetry.org | POETRY_HOME=/etc/poetry python3 - && \
  cd /usr/local/bin && \
  ln -s /etc/poetry/bin/poetry

COPY ./pyproject.toml ./poetry.lock* /app/

RUN poetry install

COPY ./prestart.sh /app/

COPY ./alembic.ini /app/

COPY ./app /app/

CMD ["uvicorn", "app.main:app", "--reload"]
