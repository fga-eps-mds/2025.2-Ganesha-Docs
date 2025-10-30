# 📖 Guia de Configuração do Repositório de Documentação (MkDocs)

Este guia padroniza o ambiente de desenvolvimento, garantindo que todos os membros da equipe possam editar, visualizar e publicar o conteúdo Markdown usando o **MkDocs com o tema Material**.

## 1\. ⚙️ Pré-Requisitos

Certifique-se de ter instalado no seu sistema:

  * **Python 3:** Instalado e no seu `PATH`.
  * **Git:** Instalado.

-----

## 2\. 🐍 Configuração do Ambiente Python (Venv)

É crucial isolar as dependências em um Ambiente Virtual (`venv`) para evitar conflitos com o Python do sistema.

### 2.1. Criação do Venv

Abra o terminal na raiz do repositório (`2025.2-Ganesha-Docs`) e execute:

```bash
# Cria a pasta 'venv' para isolamento
python3 -m venv venv
```

### 2.2. Ativação do Venv

**Atenção:** O prompt do seu terminal deve mostrar **`(venv)`** após a ativação.

| Sistema Operacional | Terminal (Shell) | Comando de Ativação |
| :--- | :--- | :--- |
| **Windows** | PowerShell (PS) | `.\venv\Scripts\activate` |
| **Windows** | CMD / Git Bash | `.\venv\Scripts\activate` |
| **Linux/macOS** | Bash / Zsh | `source venv/bin/activate` |

-----

## 3\. 📦 Instalação das Dependências

Com o ambiente virtual **ativo** (`(venv)` visível), instale as bibliotecas necessárias.

### 3.1. Instalação para o Primeiro Desenvolvedor (Criação do `requirements.txt`)

Se o arquivo **`requirements.txt` NÃO existir** no repositório, use estes comandos.

> **Nota:** Usamos `python -m pip` para garantir que o **pip correto** do ambiente virtual seja chamado, evitando o erro `externally-managed-environment`.

```bash
# 1. Instala MkDocs e o tema Material (e outras extensões)
(venv) $ python -m pip install mkdocs mkdocs-material

# 2. Cria o arquivo requirements.txt para o restante da equipe
(venv) $ pip freeze > requirements.txt
```

### 3.2. Instalação para o Restante da Equipe

Se o arquivo **`requirements.txt` JÁ existir** no repositório:

```bash
# Instala todas as dependências listadas no arquivo requirements.txt
(venv) $ python -m pip install -r requirements.txt
```

-----

## 4\. 📝 Fluxo de Trabalho (Escrever e Visualizar)

### 4.1. Edição e Criação

Todos os arquivos de documentação devem ser escritos em formato **Markdown (`.md`)** e salvos dentro da pasta `docs/`.

### 4.2. Configuração do Menu

Sempre que um novo arquivo for criado, edite o arquivo **`mkdocs.yml`** (na raiz do repositório) para incluí-lo na seção `nav:` e garantir que ele apareça no menu de navegação do site.

### 4.3. Visualização Local (Servidor de Desenvolvimento)

Para ver as alterações em tempo real no seu navegador, execute:

```bash
(venv) $ mkdocs serve
```

O servidor iniciará (geralmente em `http://127.0.0.1:8000/`). O MkDocs monitora arquivos e recarrega automaticamente. Para parar o servidor, volte ao terminal e pressione **`Ctrl + C`**.

-----

## 5\. 🚀 Publicação e Versionamento (Git)

Depois de verificar a documentação localmente e garantir que está pronta para ser compartilhada:

### 5.1. Publicar no GitHub Pages (Deploy)

Este comando gera o site HTML final e o envia para a *branch* de publicação (`gh-pages`).

```bash
(venv) $ mkdocs gh-deploy
```

### 5.2. Comitar o Conteúdo Fonte (Markdown)

É crucial que os arquivos Markdown fonte (`.md` e o `mkdocs.yml`) sejam comitados na *branch* de desenvolvimento/principal:

```bash
# Adiciona todos os arquivos novos e modificados (exceto os ignorados pelo .gitignore)
git add .

# Usa Conventional Commits (tipo 'docs' para documentação)
git commit -m "docs(feature): Adiciona [Breve descrição]"

# Envia para o repositório
git push origin [NOME_DA_BRANCH]
```
