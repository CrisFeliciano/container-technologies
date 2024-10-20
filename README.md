# Workflow de Criação e Scan de Imagem Docker

Este repositório contém um workflow automatizado do GitHub Actions que realiza a construção de uma imagem Docker, faz a verificação de vulnerabilidades com o Trivy e envia a imagem para o Docker Hub. Além disso, o workflow também cria um pull request automático para atualizar a branch `main` com as alterações da branch `develop`.

## Etapas do Workflow

1. **Checkout do Código**: O workflow começa fazendo o checkout do código do repositório para garantir que os arquivos necessários estejam disponíveis.

2. **Login no Docker Hub**: Autentica-se no Docker Hub utilizando as credenciais armazenadas como segredos no GitHub.

3. **Cálculo de Versão**: Utiliza o versionamento semântico para calcular automaticamente a versão da imagem Docker com base nos commits.

4. **Configuração do Docker Buildx**: O Buildx é configurado para possibilitar a construção de imagens Docker otimizadas.

5. **Construção da Imagem**: A imagem Docker é construída a partir do Dockerfile presente no repositório, utilizando a versão calculada.

6. **Scan de Vulnerabilidades com Trivy**: A imagem construída é verificada pelo Trivy, que identifica vulnerabilidades de alta e crítica severidade.

7. **Envio da Imagem ao Docker Hub**: Após a construção e verificação, a imagem é enviada para o Docker Hub.

8. **Criação de Pull Request**: Por fim, é aberto um pull request automático da branch `develop` para a `main`, sugerindo a atualização.

## Segredos Necessários

Para que o workflow funcione corretamente, os seguintes segredos precisam ser configurados no repositório:

- **DOCKERHUB_USERNAME**: Seu nome de usuário no Docker Hub.
- **DOCKERHUB_TOKEN**: Um token de acesso ou senha do Docker Hub.
- **GITHUB_TOKEN**: Token do GitHub para criar pull requests automaticamente.

Este fluxo automatiza o processo de criação e segurança de imagens Docker, garantindo que a imagem seja sempre verificada antes de ser utilizada.
