# 🛒 E-commerce API

Esta é uma API para um e-commerce, desenvolvida com Flask e Python. A API permite o gerenciamento de **usuários**, **produtos** e **carrinhos de compras**, além de operações de autenticação e autorização.

## 🛠️ Tecnologias Utilizadas 

- 🐍 **Python**: Linguagem de programação usada no desenvolvimento da API.
- ⚡ **Flask**: Framework web para Python, ideal para criar APIs rápidas.
- 🗄️ **Flask-SQLAlchemy**: Extensão para integração com bancos de dados SQL.
- 🔑 **Flask-Login**: Gerenciamento de sessões e autenticação de usuários.
- 🌍 **Flask-Cors**: Habilita o CORS (Cross-Origin Resource Sharing) para a API.
- 🔐 **Werkzeug**: Biblioteca para manipulação de requisições HTTP e segurança.
- 🔒 **cryptography**: Biblioteca para criptografia e segurança de dados.
- 🛡️ **bcrypt**: Ferramenta para hashing de senhas, garantindo segurança.
- ☁️ **AWS Elastic Beanstalk**: Plataforma para deploy e escalabilidade de aplicações Flask.
- 🛠️ **AWS CLI**: Ferramenta de linha de comando para gerenciamento de serviços AWS, incluindo deploys automatizados.

## ⚙️ Funcionalidades

- 🔑 **Login/Logout de Usuário**: Permite que os usuários se autentiquem e realizem logout de forma segura.
- 🧑‍💻 **Gerenciamento de Usuários**: Criação de novos usuários e validação de credenciais durante o login.
- 🛍️ **Catálogo de Produtos**: Visualização de produtos disponíveis no e-commerce com a capacidade de buscar e filtrar.
- 🛒 **Carrinho de Compras**: Adicionar, remover e visualizar produtos no carrinho, além de realizar o checkout.
- 🛠️ **CRUD de Produtos**: Operações completas para gerenciar produtos:
  - **📦 Adicionar Produto**: Adiciona um novo produto ao catálogo.
  - **✏️ Atualizar Produto**: Permite editar as informações de um produto existente.
  - **🔍 Visualizar Produto**: Exibe os detalhes de um produto específico.
  - **❌ Remover Produto**: Exclui um produto do catálogo.
- 🔍 **Busca de Produtos**: Pesquisa de produtos por nome ou descrição.


## 🚀 Como Rodar o Projeto

📌 1. Clone o repositório:

```bash
git clone https://github.com/joschonarth/flask-ecommerce-api.git
```

📌 2. Entre na pasta do projeto:

```bash
cd flask-ecommerce-api
```

📌 3. Crie um ambiente virtual:

```bash
python -m venv .venv
```

📌 4. Ative o ambiente ambiente virtual:

```bash
.venv\Scripts\activate
```

📌 5. Instale as dependências do projeto que estão no arquivo [`requirements.txt`](requirements.txt):

```bash
pip install -r requirements.txt
```

📌 6. Abra o `Flask Shell` no terminal e crie as tabelas no banco de dados:

- Primeiro, abra o Flask shell:

    ```bash
    flask shell
    ```
- Depois, dentro do Flask Shell, crie as tabelas:

    ```bash
    db.create_all()
    ```
- Salve as alterações no banco de dados:

    ```bash
    db.sessions.commit()
    ```
- Saia do Flask Shell:

    ```bash
    exit()
     ```

📌 7. Inicie o servidor de desenvolvimento:

```bash
python application.py
```

## 🌐 Acesso à API
A API estará disponível em: [http://127.0.0.1:5000](http://127.0.0.1:5000)


## 🌐 Endpoints

### 👤 Usuário

#### 📝 Registrar Novo Usuário
- **Descrição**: Registra um novo usuário no sistema.
- **Método**: `POST`
- **Endpoint**: `/api/users`
- **Corpo da Requisição**:
```json
{
  "username": "<string>",
  "password": "<string>"
}
```

#### 🔑 Login do Usuário
- **Descrição**: Autentica um usuário e inicia uma sessão.
- **Método**: `POST`
- **Endpoint**: `/login`
- **Corpo da Requisição**:
```json
{
  "username": "<string>",
  "password": "<string>"
}
```

#### 🚪 Logout do Usuário
- **Descrição**: Finaliza a sessão do usuário autenticado.
- **Método**: `POST`
- **Endpoint**: `/logout`

---

### 🛒 Produtos

#### ➕ Adicionar Produto
- **Descrição**: Adiciona um novo produto ao catálogo (requer login).
- **Método**: `POST`
- **Endpoint**: `/api/products/add`
- **Corpo da Requisição**:
```json
{
  "id": "<integer>",
  "name": "<string>",
  "price": "<number>",
  "description": "<string>"
}
```

#### ❌ Remover Produto
- **Descrição**: Remove um produto do catálogo com base no seu ID (requer login).
- **Método**: `DELETE`
- **Endpoint**: `/api/products/delete/<int:product_id>`

#### ✏️ Atualizar Produto
- **Descrição**: Atualiza as informações de um produto existente com base no seu ID (requer login).
- **Método**: `PUT`
- **Endpoint**: `/api/products/update/<int:product_id>`
- **Corpo da Requisição**:
```json
{
  "name": "<string>",
  "price": "<number>",
  "description": "<string>"
}
```

#### 🔍 Obter Detalhes do Produto
- **Descrição**: Retorna os detalhes de um produto específico com base no seu ID.
- **Método**: `GET`
- **Endpoint**: `/api/products/<int:product_id>`

#### 📋 Listar Produtos
- **Descrição**: Retorna uma lista de todos os produtos disponíveis no catálogo.
- **Método**: `GET`
- **Endpoint**: `/api/products`

---

### 🛍️ Carrinho

#### ➕ Adicionar ao Carrinho
- **Descrição**: Adiciona um produto ao carrinho do usuário autenticado com base no ID do produto (requer login).
- **Método**: `POST`
- **Endpoint**: `/api/cart/add/<int:product_id>`

#### ❌ Remover do Carrinho
- **Descrição**: Remove um produto do carrinho do usuário autenticado com base no ID do produto (requer login).
- **Método**: `DELETE`
- **Endpoint**: `/api/cart/remove/<int:product_id>`

#### 🛒 Visualizar Carrinho
- **Descrição**: Retorna o conteúdo do carrinho do usuário autenticado (requer login).
- **Método**: `GET`
- **Endpoint**: `/api/cart`

#### ✅ Finalizar Compra (Checkout)
- **Descrição**: Finaliza a compra e esvazia o carrinho do usuário autenticado (requer login).
- **Método**: `POST`
- **Endpoint**: `/api/cart/checkout`

## Contribuições 🌟

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue com sugestões ou enviar um pull request com melhorias.

## 📞 Contato 

<div>
    <a href="https://www.linkedin.com/in/joschonarth/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a>
    <a href="mailto:joschonarth@gmail.com" target="_blank"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
</div>