# 📖 Guia de Configuração do Repositório de Documentação (MkDocs)

Este guia padroniza o ambiente de desenvolvimento para a documentação, garantindo que todos os membros da equipe possam editar, visualizar e publicar o conteúdo Markdown usando o MkDocs.

## 1. ⚙️ Pré-Requisitos

Antes de começar, certifique-se de que você tem:

* **Python 3:** Instalado e no seu `PATH`.
* **Git:** Instalado.

## 2. 🐍 Configuração do Ambiente Python (Venv)

É fundamental isolar as dependências da documentação usando um Ambiente Virtual (`venv`).

### 2.1. Criação do Venv

Abra o terminal na raiz do repositório (`2025.2-Ganesha-Docs`) e execute:

```bash
# Cria a pasta 'venv' para isolamento
python -m venv venv
```

### 2.2. Ativação do Venv

**Atenção:** O comando de ativação depende do seu sistema operacional e terminal. O prompt do seu terminal deve mostrar **(venv)** após a ativação.

| Sistema Operacional | Terminal (Shell) | Comando de Ativação |
| :--- | :--- | :--- |
| Windows | PowerShell (PS) | `.\venv\Scripts\activate` |
| Windows | CMD / Git Bash | | `venv\Scripts\activate` |
| Linux/macOS | Bash / Zsh | `source venv/bin/activate` |

### 3. 📦 Instalação das Dependências (MkDocs)

Como você notou, o `requirements.txt` pode não existir inicialmente. O guia deve priorizar a criação dele e, em seguida, o uso. Com o ambiente virtual **ativo** (`(venv)` visível no terminal), instale as bibliotecas necessárias.

#### 3.1. Instalação e Criação do `requirements.txt` (Para o Primeiro Desenvolvedor)

Se o arquivo `requirements.txt` **NÃO existir** no repositório, use estes comandos:

```bash
# 1. Instala MkDocs e o tema Material (e outras extensões)
(venv) $ pip install mkdocs mkdocs-material

# 2. Cria o arquivo requirements.txt para o restante da equipe
(venv) $ pip freeze > requirements.txt
```
### 2.2. Ativação do Venv

**Atenção:** O comando de ativação depende do seu sistema operacional e terminal. O prompt do seu terminal deve mostrar **(venv)** após a ativação.

| Sistema Operacional | Terminal (Shell) | Comando de Ativação |
| :--- | :--- | :--- |
| Windows | PowerShell (PS) | `.\venv\Scripts\activate` |
| Windows | CMD / Git Bash | | `venv\Scripts\activate` |
| Linux/macOS | Bash / Zsh | `source venv/bin/activate` |

### 3. 📦 Instalação das Dependências (MkDocs)

Como você notou, o `requirements.txt` pode não existir inicialmente. O guia deve priorizar a criação dele e, em seguida, o uso. Com o ambiente virtual **ativo** (`(venv)` visível no terminal), instale as bibliotecas necessárias.

#### 3.1. Instalação e Criação do `requirements.txt` (Para o Primeiro Desenvolvedor)

Se o arquivo `requirements.txt` **NÃO existir** no repositório, use estes comandos:

```bash
# 1. Instala MkDocs e o tema Material (e outras extensões)
(venv) $ pip install mkdocs mkdocs-material

# 2. Cria o arquivo requirements.txt para o restante da equipe
(venv) $ pip freeze > requirements.txt
```

3.2. Instalação para o Restante da Equipe
Se o arquivo requirements.txt JÁ existir no repositório:

```bash
# Instala todas as dependências listadas no arquivo requirements.txt
(venv) $ pip install -r requirements.txt
```
4. 📝 Fluxo de Trabalho (Escrever e Visualizar)
#### 4.1. Edição e Criação
Todos os arquivos de documentação devem ser escritos em formato Markdown (.md) e salvos dentro da pasta docs/.

#### 4.2. Configuração do Menu
Sempre que um novo arquivo for criado, edite o arquivo mkdocs.yml (na raiz do repositório) para incluí-lo na seção nav: e garantir que ele apareça no menu de navegação.

#### 4.3. Visualização Local
Para ver as alterações em tempo real no seu navegador:

```bash
(venv) $ mkdocs serve
```
Com certeza! Aqui está o trecho formatado em Markdown, com o bloco de código Bash devidamente aninhado:

Markdown

O servidor iniciará (geralmente em http://127.0.0.1:8000/). Para parar o servidor, volte ao terminal e pressione Ctrl + C. O MkDocs monitora arquivos e recarrega automaticamente.

### 5. 🚀 Publicação e Versionamento (Git)
Depois de verificar a documentação localmente e garantir que está pronta para ser compartilhada:

#### 5.1. Publicar no GitHub Pages (Deploy)
Este comando gera o site HTML final e o envia para a branch de publicação (gh-pages).

```bash
(venv) $ mkdocs gh-deploy
```

#### 5.2. Comitar o Conteúdo Fonte (Markdown)
É crucial que os arquivos Markdown fonte (.md e o mkdocs.yml) sejam comitados na branch de desenvolvimento/principal:

```bash
# Adiciona todos os arquivos novos e modificados (exceto os ignorados pelo .gitignore)
git add .
# Usa Conventional Commits (tipo 'docs' para documentação)
git commit -m "docs(feature): Adiciona [Breve descrição]"
# Envia para o repositório
git push origin [NOME_DA_BRANCH]
```


