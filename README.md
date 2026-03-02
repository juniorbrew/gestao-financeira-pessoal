# 💰 Gestão Financeira Pessoal

Sistema SaaS profissional de gestão financeira pessoal com arquitetura multi-tenant, regras financeiras corretas e pronto para produção.

## ✨ Características

- 🏢 **Multi-tenant** - Cada cliente com dados isolados
- 👥 **Múltiplos usuários** - Suporte a diferentes roles (owner, admin, member)
- 💳 **Gestão de cartão de crédito** - Separação correta de compras e faturas
- 📊 **Dashboard profissional** - Visualizações e indicadores
- 📈 **Gráficos avançados** - Análise de gastos e receitas
- 🎯 **Orçamentos e metas** - Controle financeiro completo
- 🔔 **Sistema de alertas** - Notificações inteligentes
- 🔐 **Segurança** - Hash de senhas, JWT, isolamento por tenant
- 🚀 **Pronto para produção** - Docker, migrations, índices de performance

## 🏗️ Arquitetura

### Stack Tecnológico

- **Backend:** NestJS + TypeScript + PostgreSQL
- **Frontend:** Next.js + React + TailwindCSS
- **Autenticação:** JWT + bcrypt
- **Containerização:** Docker Compose

### Estrutura de Pastas

```
gestao-financeira-pessoal/
├── apps/
│   ├── backend/          # API NestJS
│   │   ├── src/
│   │   │   ├── auth/
│   │   │   ├── tenants/
│   │   │   ├── users/
│   │   │   ├── accounts/
│   │   │   ├── transactions/
│   │   │   ├── categories/
│   │   │   ├── credit-cards/
│   │   │   ├── bills/
│   │   │   ├── budgets/
│   │   │   ├── goals/
│   │   │   ├── dashboard/
│   │   │   ├── common/
│   │   │   └── database/
│   │   ├── test/
│   │   ├── Dockerfile
│   │   ├── package.json
│   │   └── tsconfig.json
│   └── frontend/         # App Next.js
│       ├── src/
│       │   ├── app/
│       │   ├── components/
│       │   ├── hooks/
│       │   ├── services/
│       │   └── styles/
│       ├── Dockerfile
│       ├── package.json
│       └── tsconfig.json
├── docker-compose.yml
├── .env.example
├── .gitignore
├── package.json
└── README.md
```

## 🚀 Quick Start

### Pré-requisitos

- Docker e Docker Compose
- Node.js 18+ (para desenvolvimento local)
- PostgreSQL 16+ (ou usar Docker)

### Instalação com Docker

1. Clone o repositório:
```bash
git clone https://github.com/juniorbrew/gestao-financeira-pessoal.git
cd gestao-financeira-pessoal
```

2. Configure as variáveis de ambiente:
```bash
cp .env.example .env
```

3. Inicie os serviços:
```bash
docker-compose up -d
```

4. Acesse a aplicação:
- Frontend: http://localhost:3001
- API: http://localhost:3000
- Banco de dados: localhost:5432

### Instalação Local

1. Instale as dependências:
```bash
yarn install
```

2. Configure o banco de dados:
```bash
cd apps/backend
yarn typeorm migration:run
```

3. Inicie os servidores:
```bash
yarn dev
```

## 📊 Schema do Banco de Dados

### Tabelas Principais

- **tenants** - Organizações/workspaces
- **users** - Usuários do sistema
- **accounts** - Contas bancárias (corrente, poupança, etc)
- **transactions** - Movimentações financeiras
- **categories** - Categorias de receita/despesa
- **credit_cards** - Cartões de crédito
- **bills** - Faturas de cartão
- **budgets** - Orçamentos por categoria
- **goals** - Metas financeiras

### Regras Financeiras

1. **Receita** - Aumenta saldo da conta
2. **Despesa** - Reduz saldo da conta
3. **Transferência** - Cria saída em uma conta e entrada em outra
4. **Compra Cartão** - Não altera saldo, vai para fatura
5. **Pagamento Fatura** - Reduz saldo e marca fatura como paga
6. **Status** - Apenas transações "paid" alteram saldo

## 🔐 Segurança

- ✅ Hash bcrypt para senhas
- ✅ JWT para autenticação
- ✅ Isolamento de dados por tenant_id
- ✅ Validação de permissões por role
- ✅ CORS configurado
- ✅ Rate limiting

## 📚 Documentação

- [API Documentation](./docs/API.md) - Endpoints e exemplos
- [Database Schema](./docs/DATABASE.md) - Estrutura completa
- [Financial Rules](./docs/FINANCIAL_RULES.md) - Regras de negócio
- [Architecture](./docs/ARCHITECTURE.md) - Decisões técnicas

## 🛣️ Roadmap

### MVP (Fase 1)
- [x] Setup inicial
- [ ] Autenticação e cadastro
- [ ] CRUD de contas
- [ ] CRUD de transações
- [ ] Dashboard básico

### Phase 2
- [ ] Cartões de crédito
- [ ] Faturas
- [ ] Categorias
- [ ] Gráficos

### Phase 3
- [ ] Orçamentos
- [ ] Metas
- [ ] Alertas
- [ ] Relatórios avançados

## 🤝 Contribuindo

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📝 Licença

Este projeto está sob a licença MIT.

## 👨‍💻 Autor

**juniorbrew** - [GitHub](https://github.com/juniorbrew)

## 📧 Contato

Para dúvidas ou sugestões, abra uma issue no repositório.

---

**Desenvolvido com ❤️ por juniorbrew