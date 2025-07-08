FROM python:3.12.3-slim-bookworm

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV PIP_NO_CACHE_DIR=1

WORKDIR /app

# OSパッケージ（必要に応じて調整）
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    gcc \
    libpq-dev \
    curl \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# requirements.txt をコピーしてインストール
COPY requirements.txt .

# 仮想環境は使わず直接 pip install
RUN pip install --upgrade pip && pip install -r requirements.txt

# アプリケーション本体をコピー
COPY . .

EXPOSE 8000
