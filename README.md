Backend API - Project Root

1. Descrição
Este projeto é uma API backend desenvolvida em Node.js utilizando Express e Sequelize, com integração a banco de dados relacional (PostgreSQL). A aplicação segue uma arquitetura organizada em camadas (controllers, services, models, routes), com foco em escalabilidade, manutenção e separação de responsabilidades.

A API fornece funcionalidades para gerenciamento de usuários, autenticação, categorias e produtos, incluindo suporte a opções e imagens de produtos.

2. Tecnologias Utilizadas
Runtime: Node.js (v16+)

Framework: Express

ORM: Sequelize

Banco de Dados: PostgreSQL

Autenticação: JWT (JSON Web Token) e Bcrypt para hashing de senhas

Documentação: Swagger (OpenAPI)

Testes: Jest e Supertest

3. Requisitos e Instalação
3.1. Pré-requisitos
Node.js instalado.

Instância do PostgreSQL em execução.

Gerenciador de pacotes NPM ou Yarn.

3.2. Instalação
Clone o repositório:

Bash
git clone <url-do-repositorio>
cd project-root
Instale as dependências:

Bash
npm install

4. Configuração e Execução
4.1. Variáveis de Ambiente
Crie um arquivo .env na raiz do projeto e configure as seguintes variáveis:

Snippet de código
DB_HOST=localhost
DB_USER=seu_usuario
DB_PASS=sua_senha
DB_NAME=nome_do_banco
DB_PORT=5432
JWT_SECRET=sua_chave_secreta
4.2. Banco de Dados
Execute as migrações para criar as tabelas no PostgreSQL:

Bash
npx sequelize-cli db:migrate
4.3. Scripts Disponíveis
Desenvolvimento: npm run dev (executa com Nodemon para recarregamento automático).

Produção: npm start (executa o servidor de forma estável).

Testes: npm test (executa a suíte de testes com Jest).

5. Estrutura do Projeto
O projeto segue uma estrutura modular para facilitar a manutenção:

Plaintext
src/
├── app.js           # Configuração principal do Express
├── server.js        # Inicialização do servidor
├── config/          # Configurações de banco de dados e globais
├── controllers/     # Lógica de controle e resposta das rotas
├── services/        # Regras de negócio e comunicação com o DB
├── models/          # Definição das tabelas (Sequelize)
├── database/        # Migrations e sementes do banco
├── routes/          # Definição de endpoints da API
└── middleware/      # Interceptadores (Autenticação, Logs, etc.)

6. Documentação e Uso da API
6.1. Swagger
Com a aplicação rodando, acesse a documentação interativa em:
http://localhost:3000/api-docs

6.2. Exemplos de Requisição
Autenticação (POST /login)

Payload:

JSON
{
  "email": "usuario@email.com",
  "password": "senha"
}
Resposta: {"token": "jwt_token_aqui"}

Acesso a Rotas Protegidas
Para rotas que exigem login, inclua o token no Header:
Authorization: Bearer <seu_token_aqui>

7. Boas Práticas Adotadas
Separação de Responsabilidades: Arquitetura inspirada em MVC com camada extra de Services.

Segurança: Proteção de dados sensíveis via .env e senhas criptografadas com Bcrypt.

Escalabilidade: Estrutura de pastas preparada para o crescimento modular.

Confiabilidade: Cobertura de funcionalidades através de testes automatizados.

8. Licença
Este projeto está sob a licença ISC.