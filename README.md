
# Exemplo GitHub Actions: Jobs com Artefatos

Este exemplo mostra como criar múltiplos jobs no GitHub Actions usando artefatos.

### ✨ O que faz

- **Pipeline** (`jobs examples`):
  - É acionado manualmente pelo botão **Run workflow** (`workflow_dispatch`).
  - Possui dois jobs: `build` e `deploy`.

### 🏗 Jobs

- **Job: build**
  - Roda em Ubuntu.
  - Cria um arquivo chamado `build-result.txt` com o conteúdo `"Full featured artifact"`.
  - Faz upload do arquivo como um artefato usando `actions/upload-artifact`.

- **Job: deploy**
  - Só roda se a mensagem do commit contiver `[deploy]`.
  - Depende do job `build` (`needs: build`).
  - Faz download do artefato `build-result.txt` usando `actions/download-artifact`.
  - Lista o arquivo baixado com o comando `ls`.

### 📂 Estrutura

```
.github/
└── workflows/
    └── jobs-examples.yml
```

### 💡 Para que serve

👉 Use este modelo como base para:
- Dividir workflows em múltiplos jobs encadeados.
- Compartilhar arquivos (artefatos) entre jobs.
- Condicionar a execução de jobs com base em mensagens de commit ou outros critérios.
