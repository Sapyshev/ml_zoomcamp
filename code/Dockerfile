FROM python:3.11-slim

RUN pip install pipenv

WORKDIR /app
COPY Pipfile Pipfile.lock /app/

RUN pipenv install --system --deploy
COPY predict.py model_C=1.0.bin /app/

EXPOSE 9696
ENTRYPOINT ["gunicorn", "--bind=0.0.0.0:9696", "predict:app"]