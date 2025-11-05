# 🚀 Guia de Configuração e Desenvolvimento Local

Este guia descreve os passos necessários para configurar o ambiente de desenvolvimento local (**Backend Python/Flask**) e iniciar o servidor de banco de dados **MySQL** usando **Docker**.

---

## ✅ Pré-requisitos

Certifique-se de ter instalado em sua máquina:

- **Python 3.10+**
- **Git**
- **Docker Desktop** (para Windows/macOS) ou **Docker Engine** (para Linux)
- **MySQL Workbench** ou outro cliente SQL (opcional, para visualização do DB).

---

## 🔹 Passo 1: Configuração do Ambiente Python

### 1. Clonar o Repositório e Navegar

```bash
git clone https://github.com/fga-eps-mds/2025.2-ganesha
cd 2025.2-Ganesha/
```

---

### 2. Criar e Ativar o Ambiente Virtual (venv)

Execute os comandos na raiz do projeto (`2025.2-Ganesha/`):

```powershell
# Cria o ambiente virtual
python -m venv venv

# Ativa o ambiente virtual (PowerShell)
.\venv\Scripts\Activate.ps1
```

---

### 3. Instalar as Dependências

Instale todas as bibliotecas necessárias para o backend:

```powershell
(venv) PS ...> python -m pip install -r backend/requirements.txt
```

---

### 4. Configurar Variáveis de Ambiente

Copie o arquivo de exemplo (`.env.example`) para criar seu arquivo de ambiente local (`.env`) e preencha as credenciais:

```powershell
(venv) PS ...> copy .env.example .env
```

Verifique se seu `.env` contém as seguintes chaves:

```env
# ...
DB_HOST=127.0.0.1
DB_PORT=3307  # Porta mapeada do Docker
DB_NAME=ganesha_db # O nome do DB que será criado
DB_USER=root
DB_PASSWORD=ganesha123
FLASK_APP=backend/src/app # Necessário para o comando 'flask'
# ...
```

---

## 🔹 Passo 2: Inicialização do Banco de Dados (Docker)

O servidor MySQL rodará como um contêiner isolado na porta **3307**.

### 1. Rodar o Contêiner MySQL

Execute este comando na raiz do projeto para iniciar o contêiner e criar o banco de dados inicial (`ganesha_db`):

```powershell
docker run --name ganesha-mysql `
  -e MYSQL_ROOT_PASSWORD=ganesha123 `
  -e MYSQL_DATABASE=ganesha_db `
  -p 3307:3306 `
  -d mysql:8.0
```

---

### 2. Verificar Status

Confirme se o contêiner está rodando:

```powershell
docker ps
```

O status de `ganesha-mysql` deve ser **Up ...**.

---

## 🔹 Passo 3: Criação e Sincronização das Tabelas (Flask-Migrate)

### 1. Definir a Variável FLASK_APP (Obrigatório no PowerShell)

```powershell
$env:FLASK_APP="backend/src/app"
```

---

### 2. Aplicar Migrações

Execute o comando **upgrade** para criar as tabelas no seu `ganesha_db`.

> **Nota:** O `db init` e o `db migrate` são passos que você executa apenas ao criar ou alterar modelos. O `db upgrade` é a sua rotina pós-`git pull`.

```powershell
(venv) PS ...> python -m flask db upgrade
```

**Saída esperada:** Confirmação de que a(s) migração(ões) pendente(s) foram executadas, e as tabelas agora existem no DB.

---

## 🔹 Passo 4: Rodar o Servidor Local

Com o DB configurado e as tabelas criadas, você pode iniciar o backend:

```powershell
(venv) PS ...> python backend/src/app.py
```

O servidor estará rodando em:

```
http://127.0.0.1:5000/
```

---

## 🔄 Fluxo de Trabalho de Alteração de Banco de Dados

Sempre que você (ou um colega) adicionar ou alterar um modelo (tabela/coluna), siga estes passos:

1. **Mudar o Código:** Modificar a classe `Usuario` (ou criar uma nova) em `backend/src/model/`.
2. **Gerar Migração:**  
   ```powershell
   python -m flask db migrate -m "Descrição da mudança"
   ```
3. **Aplicar Migração:**  
   ```powershell
   python -m flask db upgrade
   ```

---

## 🔹 Passo 5: Visualização do Banco de Dados (MySQL Workbench)

Para visualizar e inspecionar as tabelas criadas (como `usuario` e `alembic_version`), configure uma nova conexão:

### 1. Inicie o MySQL Workbench

### 2. Crie uma Nova Conexão

Clique no sinal **+** (mais) ao lado de **MySQL Connections**.

### 3. Preencha os Campos da Conexão

| Campo             | Valor                     |
|-------------------|---------------------------|
| Connection Name   | Ganesha Local Docker     |
| Connection Method | Standard (TCP/IP)        |
| Hostname          | 127.0.0.1               |
| Port              | 3307                    |
| Username          | root                    |
| Password          | ganesha123              |
| Default Schema    | ganesha_db              |

---

### 4. Testar e Conectar

Clique em **Test Connection**.  
Após o sucesso, clique em **OK** para salvar a conexão.  
Abra a conexão e navegue no schema `ganesha_db` para ver as tabelas.

---

✅ Agora seu ambiente está pronto para desenvolvimento!
