# 🛒 E-commerce API

Esta é uma API para um e-commerce, desenvolvida com Flask e Python. A API permite o gerenciamento de **usuários**, **produtos** e **carrinhos de compras**, além de operações de autenticação e autorização.

## 🛠️ Tecnologias Utilizadas

- **Flask** - Framework web
- **Flask SQLAlchemy** - ORM para interação com o banco de dados SQLite
- **Flask CORS** - Permite requisições de origens diferentes
- **Flask Login** - Gerenciamento de autenticação de usuários
- **bcrypt** - Hash de senhas para segurança

## 📋 Funcionalidades

1. **🔑 Autenticação de Usuários**
   - Registro e login de usuários
   - Hash de senhas para segurança
   - Logout e controle de sessão

2. **📦 Gestão de Produtos**
   - Adição, remoção, atualização e visualização de produtos
   - Visualização detalhada de cada produto

3. **🛍️ Carrinho de Compras**
   - Adição e remoção de itens no carrinho
   - Visualização dos itens no carrinho
   - Finalização de compra (checkout) e limpeza do carrinho

## 🌐 Endpoints

### 👤 Usuário
- `POST /api/users` - Registrar um novo usuário
- `POST /login` - Login do usuário
- `POST /logout` - Logout do usuário

### 🛒 Produtos
- `POST /api/products/add` - Adicionar um produto (requer login)
- `DELETE /api/products/delete/<int:product_id>` - Remover um produto pelo ID (requer login)
- `PUT /api/products/update/<int:product_id>` - Atualizar dados de um produto pelo ID (requer login)
- `GET /api/products/<int:product_id>` - Obter detalhes de um produto pelo ID
- `GET /api/products` - Listar todos os produtos

### 🛍️ Carrinho
- `POST /api/cart/add/<int:product_id>` - Adicionar um produto ao carrinho do usuário (requer login)
- `DELETE /api/cart/remove/<int:product_id>` - Remover um produto do carrinho pelo ID (requer login)
- `GET /api/cart` - Visualizar o carrinho do usuário (requer login)
- `POST /api/cart/checkout` - Finalizar a compra e esvaziar o carrinho (requer login)

