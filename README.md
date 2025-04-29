# 📚 CMS For QA's - API RESTful

API de gestão de conteúdo para equipes de qualidade com autenticação JWT e CRUD completo.

## 🚀 Começando

### Pré-requisitos
- Node.js v14+
- npm ou yarn
- Banco de dados configurado (consulte `.env.example`)

### Instalação
```bash
git clone https://github.com/seu-usuario/cms-for-qas-api.git

cd cms-for-qas-api

npm install

cp .env.example .env  # Configure suas variáveis

npm run dev

POST /auth/login
{
  "email": "usuario@exemplo.com",
  "senha": "suaSenhaSegura"
}

Header necessário para rotas protegidas:

Authorization: Bearer <token-jwt>

📡 Endpoints Principais

👥 Usuários
Método	Endpoint	Descrição
POST	/usuarios	Cria novo usuário
GET	/usuarios	Lista com filtros
GET	/usuarios/:id	Busca por ID

📂 Categorias
Método	Endpoint	Descrição
POST	/categorias	Cria nova categoria
DELETE	/categorias/:id	Remove (sem artigos)

📝 Artigos
Método	Endpoint	Query Params
GET	/artigos	page, limit
POST	/artigos	Requer autorId

🗃 Modelos de Dados
typescript

interface Artigo {
  id: string;
  titulo: string;      // Máx 100 chars
  conteudo: string;
  autorId: string;     // Relacionamento
}

⚠️ Regras de Negócio

    🔒 Todos endpoints (exceto /usuarios e /auth/login) requerem JWT

    🚫 Não permite exclusão de:

        Usuários com artigos

        Categorias com artigos

    ✉️ Email de usuário deve ser único

    🏷️ Nome de categoria deve ser único

❌ Padrão de Erros
json

{
  "sucesso": false,
  "erro": "Falha na validação",
  "detalhes": [
    {
      "campo": "email",
      "mensagem": "Deve ser um email válido"
    }
  ]
}

🤝 Como Contribuir

    Faça um fork do projeto

    Crie sua branch (git checkout -b feature/incrivel)

    Commit (git commit -m 'Adiciona feature incrível')

    Push (git push origin feature/incrivel)

    Abra um Pull Request

📄 Licença MIT - Consulte LICENSE para detalhes.


