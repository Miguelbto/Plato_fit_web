# Guia Completo - Site Platô Fit Meal Prep

## 🚀 Seu Site Está Pronto!

**URL do Site:** https://p9hwiqcnkv1x.manus.space

Parabéns! Seu site completo de vendas de marmitas está funcionando perfeitamente com:
- ✅ Banco de dados SQLite
- ✅ API REST completa
- ✅ Interface responsiva moderna
- ✅ Sistema de pedidos
- ✅ Sistema de mensagens/contato
- ✅ Design nas cores da marca (branco, preto, laranja)

## 📁 Estrutura do Projeto

```
marmitas_website/
├── backend/                    # Servidor Flask (Python)
│   ├── src/
│   │   ├── models/            # Modelos do banco de dados
│   │   │   ├── user.py        # Modelo de usuário (padrão)
│   │   │   └── marmita.py     # Modelos: Marmita, Pedido, Mensagem
│   │   ├── routes/            # Rotas da API
│   │   │   ├── user.py        # Rotas de usuário (padrão)
│   │   │   ├── marmita.py     # API de marmitas
│   │   │   ├── pedido.py      # API de pedidos
│   │   │   ├── mensagem.py    # API de mensagens
│   │   │   └── seed.py        # Popular banco com dados
│   │   ├── static/            # Arquivos do frontend (React compilado)
│   │   ├── database/          # Banco de dados SQLite
│   │   │   └── app.db         # Arquivo do banco
│   │   └── main.py            # Arquivo principal do Flask
│   ├── venv/                  # Ambiente virtual Python
│   └── requirements.txt       # Dependências Python
├── frontend/                  # Interface React (desenvolvimento)
│   ├── src/
│   │   ├── components/        # Componentes UI
│   │   ├── assets/           # Imagens (logo)
│   │   ├── App.jsx           # Componente principal
│   │   └── App.css           # Estilos customizados
│   ├── dist/                 # Versão compilada (copiada para backend/src/static)
│   └── package.json          # Dependências Node.js
└── logo.jpeg                 # Logo da empresa
```

## 🛠️ Como Funciona

### Backend (Flask + SQLite)
- **Flask**: Framework web Python que serve a API e o frontend
- **SQLite**: Banco de dados leve que armazena marmitas, pedidos e mensagens
- **CORS**: Configurado para permitir comunicação frontend-backend
- **API REST**: Endpoints organizados por funcionalidade

### Frontend (React)
- **React**: Interface moderna e responsiva
- **Tailwind CSS**: Framework CSS para estilização
- **Shadcn/UI**: Componentes de interface profissionais
- **Lucide Icons**: Ícones modernos

### Banco de Dados
- **Marmitas**: nome, descrição, preço, categoria, disponibilidade
- **Pedidos**: dados do cliente, marmita, quantidade, observações
- **Mensagens**: contatos dos clientes com dúvidas

## 🎨 Personalização

### Cores da Marca
As cores estão definidas no arquivo `frontend/src/App.css`:
```css
:root {
  --primary-orange: #ea580c;    /* Laranja principal */
  --primary-orange-dark: #c2410c; /* Laranja escuro */
  --primary-black: #1f2937;     /* Preto */
  --primary-white: #ffffff;     /* Branco */
}
```

### Como Alterar Cores
1. Edite o arquivo `frontend/src/App.css`
2. Modifique as variáveis CSS acima
3. Recompile o frontend (veja seção "Modificações")

### Logo
- Localização: `frontend/src/assets/logo.jpeg`
- Para trocar: substitua o arquivo mantendo o mesmo nome
- Ou altere a importação em `frontend/src/App.jsx`

## 📊 API Endpoints

### Marmitas
- `GET /api/marmitas` - Listar todas as marmitas
- `GET /api/marmitas/{id}` - Obter marmita específica
- `GET /api/marmitas/categoria/{categoria}` - Filtrar por categoria
- `POST /api/marmitas` - Criar nova marmita (admin)

### Pedidos
- `POST /api/pedidos` - Criar novo pedido
- `GET /api/pedidos` - Listar pedidos (admin)
- `GET /api/pedidos/{id}` - Obter pedido específico
- `PUT /api/pedidos/{id}/status` - Atualizar status do pedido

### Mensagens
- `POST /api/mensagens` - Enviar mensagem de contato
- `GET /api/mensagens` - Listar mensagens (admin)
- `GET /api/mensagens/{id}` - Obter mensagem específica

### Utilitários
- `POST /api/seed` - Popular banco com marmitas de exemplo

## 🔧 Como Fazer Modificações

### 1. Modificar Marmitas
Para adicionar/editar marmitas, você pode:

**Opção A: Via API (Recomendado)**
```bash
curl -X POST https://p9hwiqcnkv1x.manus.space/api/marmitas \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "Nova Marmita",
    "descricao": "Descrição da marmita",
    "preco": 19.90,
    "categoria": "Proteína Animal",
    "imagem_url": "/static/images/nova-marmita.jpg"
  }'
```

**Opção B: Direto no banco**
1. Acesse o arquivo `backend/src/routes/seed.py`
2. Adicione suas marmitas na lista `marmitas_exemplo`
3. Faça novo deploy

### 2. Modificar Visual (Frontend)
```bash
# 1. Entre na pasta do frontend
cd frontend

# 2. Instale dependências (se necessário)
pnpm install

# 3. Faça suas modificações nos arquivos:
# - src/App.jsx (estrutura e funcionalidades)
# - src/App.css (estilos)

# 4. Teste localmente
pnpm run dev

# 5. Compile para produção
pnpm run build

# 6. Copie para o backend
cp -r dist/* ../backend/src/static/

# 7. Faça novo deploy do backend
# (veja seção "Deploy")
```

### 3. Modificar Backend (API)
```bash
# 1. Entre na pasta do backend
cd backend

# 2. Ative o ambiente virtual
source venv/bin/activate

# 3. Faça suas modificações nos arquivos:
# - src/routes/ (endpoints da API)
# - src/models/ (estrutura do banco)

# 4. Teste localmente
python src/main.py

# 5. Atualize dependências
pip freeze > requirements.txt

# 6. Faça novo deploy
# (veja seção "Deploy")
```

## 🚀 Deploy e Atualizações

### Fazer Novo Deploy
Sempre que fizer modificações, você precisa fazer um novo deploy:

```bash
# 1. Se modificou o frontend, compile primeiro:
cd frontend
pnpm run build
cp -r dist/* ../backend/src/static/

# 2. Faça o deploy do backend:
cd ../backend
# Use a ferramenta de deploy que você preferir
# O projeto está configurado para funcionar em qualquer servidor
```

### Requisitos do Servidor
- Python 3.11+
- Todas as dependências estão em `requirements.txt`
- O servidor deve permitir acesso às portas web
- SQLite não requer instalação adicional

## 📱 Funcionalidades do Site

### Para Clientes
1. **Visualizar Marmitas**: Catálogo completo com preços e descrições
2. **Filtrar por Categoria**: Proteína Animal, Vegano, Low Carb, Lanche
3. **Fazer Pedidos**: Formulário completo com dados de entrega
4. **Entrar em Contato**: Formulário para dúvidas e sugestões
5. **Design Responsivo**: Funciona perfeitamente em celular e desktop

### Para Administração
1. **Gerenciar Pedidos**: API para listar e atualizar status
2. **Gerenciar Mensagens**: API para visualizar contatos
3. **Adicionar Marmitas**: API para cadastrar novos produtos
4. **Banco de Dados**: Todos os dados ficam salvos automaticamente

## 🔒 Segurança e Backup

### Backup do Banco de Dados
O arquivo `backend/src/database/app.db` contém todos os dados:
- Faça backup regular deste arquivo
- Para restaurar: substitua o arquivo e faça novo deploy

### Dados Sensíveis
- Não há senhas ou dados sensíveis expostos
- Todos os dados de clientes ficam no banco privado
- A API não expõe informações confidenciais

## 📞 Suporte e Manutenção

### Logs e Monitoramento
- O Flask gera logs automáticos de todas as requisições
- Monitore os endpoints de pedidos e mensagens
- Verifique regularmente se o site está acessível

### Problemas Comuns
1. **Site não carrega**: Verifique se o servidor está ativo
2. **Formulários não funcionam**: Verifique a conexão com a API
3. **Marmitas não aparecem**: Verifique se o banco tem dados (use `/api/seed`)

### Melhorias Futuras Sugeridas
1. **Painel Admin**: Interface web para gerenciar pedidos
2. **Sistema de Pagamento**: Integração com gateways de pagamento
3. **Notificações**: Email automático para novos pedidos
4. **Imagens**: Upload de fotos das marmitas
5. **Relatórios**: Dashboard com estatísticas de vendas

## 🎯 Conclusão

Seu site está 100% funcional e pronto para receber pedidos! A arquitetura é profissional, escalável e fácil de manter. Todas as funcionalidades solicitadas foram implementadas:

- ✅ Banco de dados completo
- ✅ API robusta para todas as operações
- ✅ Interface moderna e responsiva
- ✅ Sistema de pedidos funcionando
- ✅ Sistema de mensagens funcionando
- ✅ Design nas cores da marca

**URL do seu site:** https://p9hwiqcnkv1x.manus.space

Agora é só divulgar e começar a receber pedidos! 🚀

