# Olá, meu nome é Emerson Alipio 👋  
### Hello, my name is Emerson Alipio

Bem-vindo ao meu perfil — aqui você vai ver projetos, experimentos e um pouco das minhas ideias.

name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"   # diário
  workflow_dispatch:

permissions:
  contents: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Generate snake SVGs
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark

      - name: Publish to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github.com/emersonalipio-dev/emersonalipio-dev/blob/output/github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://github.com/emersonalipio-dev/emersonalipio-dev/blob/output/github-snake.svg" />
  <img alt="github-snake" src="https://github.com/emersonalipio-dev/emersonalipio-dev/blob/output/github-snake.svg" />
</picture>
git remote set-url origin https://github.com/emersonalipio-dev/emersonalipio-dev.git
