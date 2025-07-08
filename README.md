# Django 5.2.3 Beginners Guide

このプロジェクトは、[Simple is Better Than Complex の Django チュートリアル](https://simpleisbetterthancomplex.com/series/2017/09/04/a-complete-beginners-guide-to-django-part-1.html) を Django 5.2.3 で復習・学習するための環境です。

## 構成

- Python 3.12（Docker内）
- Django 5.2.3
- Docker / Docker Compose
- Ruff（Linter & Formatter）

## 前提条件

- [Docker](https://www.docker.com/) と [Docker Compose](https://docs.docker.com/compose/) がインストールされていること
- [`uv`](https://github.com/astral-sh/uv) がホスト側にインストールされていること

## 🚀 セットアップ手順

### 0. uv のインストール（ホストで uv pip compile に使うため）
```bash
curl -Ls https://astral.sh/uv/install.sh | sh
```

### 1. リポジトリをクローン

```bash
git clone https://github.com/your-username/django52-beginners-guide.git
cd django52-beginners-guide
```

### 2. `requirements.txt` を生成

```bash
uv pip compile requirements.in -o requirements.txt
```

> `uv` は `pip-tools` のように `.in` から `.txt` を生成する超高速ツールです。

### 3. Docker イメージをビルド & 起動

```bash
docker compose up --build
```

### 4. 初回のみ: Django プロジェクトを作成（未作成の場合）

```bash
docker compose run --rm web django-admin startproject config .
```

### 5. 開発サーバを起動（以降）

```bash
docker compose up
```

ブラウザで [http://localhost:8000](http://localhost:8000) にアクセスして確認できます。

---

## 🔧 Lint / フォーマット（ruff 使用）

```bash
docker compose run --rm web ruff format .
docker compose run --rm web ruff check .
```

---

## 📄 ディレクトリ構成（抜粋）

```
django52-beginners-guide/
├── docker/
│   └── web/
│       └── Dockerfile
├── docker-compose.yml
├── requirements.in
├── requirements.txt
├── config/            # Djangoプロジェクト
├── app/               # アプリ（例：blog など）
└── README.md
```

---

## 📦 .gitignore（一部）

```
__pycache__/
*.py[cod]
*.sqlite3
.env
.venv/
.docker/
*.log
```
