name: Python Application CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Set Up Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.10"

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt
          pip install telebot pymongo aiohttp
          pip install pymongo python-telegram-bot pyTelegramBotAPI certifi

      - name: Set Execute Permissions
        run: chmod +x * && chmod +x LEGEND

      - name: Run Application
        run: python LSRVIPDDOS.py
