FROM python:3.10-slim

ENV PYTHONUNBUFFERED=1

# Install system build tools and libraries
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    gcc \
    g++ \
    netcat-openbsd \
    libpq-dev \
    libffi-dev \
    curl \
    git \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY backend-requirements.txt ./requirements.txt
RUN pip install --upgrade pip setuptools wheel && \
    pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8000

COPY backend_entrypoint.sh /app/backend_entrypoint.sh
RUN chmod +x /app/backend_entrypoint.sh
ENTRYPOINT ["/app/backend_entrypoint.sh"]

