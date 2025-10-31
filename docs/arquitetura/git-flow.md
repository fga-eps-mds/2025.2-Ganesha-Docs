# 💾 Padrão de Versionamento (Gitflow Simplificado & Conventional Commits)

Neste projeto, adotamos o padrão **Gitflow Simplificado** para gerenciamento de branches e o **Conventional Commits** para padronização das mensagens de commit.

## 1. Fluxo de Branches (Gitflow Simplificado)

Utilizamos duas branches principais para garantir a estabilidade do código:

| Branch | Objetivo | Onde é usado |
| :--- | :--- | :--- |
| **`main`** | Versão de **produção**. O código aqui está sempre estável, testado e pronto para ser publicado. | **Publicação final** (deploy). Nunca se faz commit direto nesta branch. |
| **`develop`** | Branch de **integração**. Recebe todas as novas funcionalidades e correções. É onde o código é testado e validado antes de ir para a `main`. | **Branch base** para o desenvolvimento contínuo. |

### 1.1. Branches de Apoio

Todas as novas funcionalidades, correções de bugs ou melhorias são feitas em branches temporárias, criadas a partir de `develop`.

| Tipo | Prefixo | Criada a partir de: | Merge em: | Objetivo Principal | Exemplo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Feature** | `feature/` | `develop` | `develop` | Implementação de novas funcionalidades. | `feature/cadastro-usuario` |
| **Bugfix** | `bugfix/` | `develop` | `develop` | Correção de bugs encontrados durante o desenvolvimento. | `bugfix/erro-login-api` |
| **Hotfix** | `hotfix/` | `main` | `main` e `develop` | Correção emergencial de falhas críticas em produção. | `hotfix/corrige-falha-critica` |
| **Release** | `release/` | `develop` | `main` e `develop` | Preparação final, testes e ajuste de versão antes do deploy. | `release/v1.0.0` |
| **Spike** | `spike/` ou `experiment/` | `develop` | Opcional (apenas se bem-sucedido) | Investigar uma tecnologia, testar um conceito arriscado ou buscar soluções. | `spike/testa-integracao-kafka` |
### 1.2. Fluxo de Trabalho Git (Exemplo Feature)

```bash
# 1. Certifique-se de estar na branch de integração
git checkout develop

# 2. Crie sua nova branch de feature
git checkout -b feature/minha-nova-feature

# 3. Faça o desenvolvimento, adicione e comite suas alterações
git add .
git commit -m "feat(minha-feature): Adiciona validacao de senha minima"

# 4. Envie a feature para o repositório remoto
git push origin feature/minha-nova-feature

# 5. Abra um Pull Request (PR) no GitHub para fazer merge em 'develop'