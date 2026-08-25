# 🏡 AssistHome API - Backend

O **AssistHome API** é o serviço de backend responsável por gerenciar a lógica de negócios, persistência de dados e integrações da aplicação AssistHome. Construído com arquitetura moderna utilizando Spring Boot e Java 21.

---

## 🛠️ Tecnologias Utilizadas

- **Linguagem:** Java (JDK 21)
- **Framework:** Spring Boot 4.1.0
- **Banco de Dados:** PostgreSQL 17
- **Migrações de Banco:** Flyway
- **Documentação de API:** Swagger (SpringDoc OpenAPI 3.0.3)
- **Monitoramento:** Spring Boot Actuator
- **Gerenciador de Dependências:** Maven

---

## 📋 Pré-requisitos

Antes de começar, certifique-se de ter as seguintes ferramentas instaladas em sua máquina local:

- [Java JDK 21](https://jdk.java.net/21/) configurado no `JAVA_HOME`.
- [Docker e Docker Compose](https://www.docker.com/) (para rodar o banco de dados localmente).
- [Git](https://git-scm.com/) para versionamento.

---

## ⚙️ Configuração do Ambiente

O projeto utiliza o arquivo `application.properties` (ou `.yml`) para gerenciar as configurações. Por padrão, a aplicação já está configurada para se conectar ao banco de dados local via Docker utilizando as credenciais abaixo.

Caso precise rodar em produção, certifique-se de sobrescrever as variáveis de ambiente necessárias (como `SPRING_DATASOURCE_URL`, `SPRING_DATASOURCE_USERNAME` e `SPRING_DATASOURCE_PASSWORD`).

---

## 🐘 Como subir o Banco de Dados (Docker Compose)

O projeto inclui um arquivo `docker-compose.yml` na raiz para facilitar a inicialização do PostgreSQL.

1. Certifique-se de que o Docker Desktop (ou daemon do Docker) está em execução.
2. No terminal, na raiz do projeto, execute o comando abaixo:

   docker compose up -d

3. O banco de dados estará disponível e configurado com as seguintes credenciais:
   - **Host:** `localhost`
   - **Porta:** `5432`
   - **Database:** `assisthome`
   - **Usuário:** `assisthome`
   - **Senha:** `assisthome_dev`

---

## ▶️ Como executar o Backend Localmente

Com o banco de dados rodando, você pode iniciar a aplicação Spring Boot. O projeto utiliza o Maven Wrapper (`mvnw`), então não é necessário ter o Maven instalado globalmente.

1. No terminal, dentro da pasta do projeto, execute:

   ./mvnw spring-boot:run

2. A API iniciará na porta padrão `8080`.
   - **URL Base:** `http://localhost:8080`

---

## 🔌 Portas Utilizadas no Projeto

| Serviço | Porta | Descrição |
| :--- | :--- | :--- |
| Backend (Spring Boot) | `8080` | Porta principal da API REST |
| PostgreSQL (Docker) | `5432` | Porta de conexão com o banco |

---

## 📚 Documentação da API (Swagger)

A documentação interativa e o contrato da API foram gerados automaticamente com o SpringDoc (OpenAPI).

Com o servidor rodando, você pode acessá-los através dos links abaixo:

- **Interface Gráfica (Swagger UI):**  
  [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

- **Especificação JSON (OpenAPI 3):**  
  [http://localhost:8080/v3/api-docs](http://localhost:8080/v3/api-docs)

---

## 🛣️ Principais Endpoints

*(Substitua esta seção com as rotas reais do seu sistema. Abaixo está um exemplo)*

- `POST /api/v1/auth/login` - Autenticação de usuário.
- `GET /api/v1/users` - Lista os usuários cadastrados.
- `POST /api/v1/services` - Cria um novo serviço no AssistHome.

---

## ❤️ Monitoramento e Health Check

O Spring Boot Actuator está configurado para expor endpoints de monitoramento da saúde da aplicação. Para verificar se o serviço está operando corretamente e conectado ao banco, acesse:

- **Health Check URL:**  
  [http://localhost:8080/actuator/health](http://localhost:8080/actuator/health)

**Resposta esperada:**

    {
      "status": "UP"
    }

---

## 📌 Observações Adicionais

- **Live Reload:** O projeto possui o `spring-boot-devtools` habilitado. Alterações nos arquivos `.java` acionarão um reinício automático e rápido do servidor durante o desenvolvimento.
- **Migrations (Flyway):** Não é necessário criar as tabelas do banco manualmente. O Flyway detectará a inicialização do projeto e aplicará todos os scripts `.sql` localizados em `src/main/resources/db/migration` automaticamente.