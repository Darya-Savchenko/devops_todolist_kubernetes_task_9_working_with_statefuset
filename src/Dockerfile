# Stage 1: Build Stage
ARG PYTHON_VERSION=3.8
FROM python:${PYTHON_VERSION} as builder

# Set the working directory
WORKDIR /app
COPY . .

# Stage 2: Run Stage
FROM python:${PYTHON_VERSION} as run

WORKDIR /app

ENV PYTHONUNBUFFERED=1
ENV DB_NAME="default"
ENV DB_USER="default"
ENV DB_PASSWORD="default"
ENV DB_HOST="default"

COPY --from=builder /app .

RUN pip install --upgrade pip && \
    pip install -r requirements.txt

# RUN python manage.py migrate

# Run database migrations and start the Django application
ENTRYPOINT ["python", "manage.py", "runserver", "0.0.0.0:8080"]

