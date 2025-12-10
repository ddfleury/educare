# Educare.AI

Sistema de Acompanhamento Pedagógico Personalizado com Inteligência Artificial

## 📋 Sobre o Projeto

O **Educare.AI** é uma solução web desenvolvida em PHP que utiliza Inteligência Artificial para fornecer acompanhamento pedagógico personalizado. O sistema cruza dados de desempenho escolar, hábitos de estudo e perfil cognitivo dos alunos para gerar planos individuais de aprendizagem e fornecer recomendações inteligentes.

### Funcionalidades Principais

- **Dashboard Personalizado** para Alunos, Responsáveis e Professores
- **Gestão de Desempenho** com registro de notas e frequência
- **Hábitos de Estudo** com acompanhamento e análise
- **Perfil Cognitivo** para identificar estilo de aprendizagem
- **Planos de Aprendizagem** gerados automaticamente com IA
- **Recomendações Personalizadas** baseadas em dados do aluno
- **Indicadores de Risco** para identificar alunos que precisam de atenção

## 🛠️ Tecnologias Utilizadas

- **Backend:** PHP 8+ (MVC)
- **Frontend:** HTML5, CSS3, JavaScript, Bootstrap 5
- **Banco de Dados:** MySQL
- **Segurança:** PDO com prepared statements, password_hash

## 📁 Estrutura do Projeto

```
educare/
├── public/                 # Pasta pública (ponto de entrada)
│   ├── index.php          # Front controller
│   ├── css/
│   ├── js/
│   └── uploads/
├── app/
│   ├── controllers/       # Controllers (lógica de negócio)
│   ├── models/           # Models (acesso a dados)
│   ├── views/            # Views (interface)
│   └── core/             # Classes base (Router, Controller, Model)
├── config/               # Configurações
│   ├── config.php
│   └── database.php
└── sql/
    └── schema.sql        # Script de criação do banco
```

## 🚀 Instalação

### Pré-requisitos

- PHP 8.0 ou superior
- MySQL 5.7 ou superior
- Apache com mod_rewrite habilitado (ou servidor compatível)
- XAMPP, WAMP, LAMP ou servidor similar

### Passo a Passo

1. **Clone ou baixe o projeto**
   ```bash
   # Se estiver usando Git
   git clone <url-do-repositorio>
   cd educare
   ```

2. **Configure o banco de dados**
   
   - Abra o phpMyAdmin ou cliente MySQL
   - Importe o arquivo `sql/schema.sql` para criar o banco de dados e as tabelas
   - Ou execute via linha de comando:
     ```bash
     mysql -u root -p < sql/schema.sql
     ```

3. **Configure a conexão com o banco**
   
   Edite o arquivo `config/database.php` e ajuste as credenciais:
   ```php
   private const HOST = 'localhost';
   private const DB_NAME = 'educare_ai';
   private const USERNAME = 'root';      // Seu usuário MySQL
   private const PASSWORD = '';          // Sua senha MySQL
   ```

4. **Configure a URL base**
   
   Edite o arquivo `config/config.php` e ajuste a constante `BASE_URL`:
   ```php
   define('BASE_URL', 'http://localhost/educare/public');
   ```
   
   **Importante:** Ajuste conforme seu ambiente:
   - XAMPP: `http://localhost/educare/public`
   - WAMP: `http://localhost/educare/public`
   - Servidor local: `http://localhost:8000` (se usar servidor PHP built-in)

5. **Configure o servidor web**
   
   **Opção A - Apache (XAMPP/WAMP):**
   - Coloque a pasta `educare` em `htdocs` (XAMPP) ou `www` (WAMP)
   - Certifique-se de que o mod_rewrite está habilitado
   - O arquivo `.htaccess` já está configurado
   
   **Opção B - Servidor PHP Built-in:**
   ```bash
   cd public
   php -S localhost:8000
   ```
   Acesse: `http://localhost:8000`

6. **Permissões (Linux/Mac)**
   ```bash
   chmod -R 755 public/uploads
   ```

## 📖 Como Usar

### Primeiro Acesso

1. Acesse o sistema no navegador: `http://localhost/educare/public`
2. Você será redirecionado para a página de login
3. Clique em "Cadastre-se" para criar uma conta

### Criando Contas

**Aluno:**
- Preencha os dados pessoais
- Informe escola, série e turma
- Após o cadastro, faça login

**Responsável:**
- Cadastre-se como responsável
- Informe o relacionamento com o aluno
- Após o cadastro, será necessário vincular ao aluno (via banco de dados ou interface futura)

**Professor:**
- Cadastre-se como professor
- Informe a disciplina que leciona
- Após o cadastro, será necessário vincular aos alunos (via banco de dados ou interface futura)

### Fluxo Básico

1. **Aluno faz login**
2. **Cadastra hábitos de estudo** (menu: Hábitos de Estudo)
3. **Preenche perfil cognitivo** (menu: Perfil Cognitivo)
4. **Professor cadastra notas** (menu: Cadastrar Notas)
5. **Sistema gera plano de aprendizagem** (menu: Planos de Aprendizagem > Gerar Novo Plano)
6. **Aluno visualiza recomendações** no dashboard e no plano

## 🔐 Segurança

- Senhas são armazenadas com `password_hash()` (bcrypt)
- Todas as queries usam PDO com prepared statements
- Proteção contra SQL Injection
- Sessões seguras
- Validação de inputs

## 🧠 Motor de IA Simplificado

O sistema utiliza um motor de IA simplificado que:

1. **Analisa o desempenho** do aluno (médias por disciplina)
2. **Considera hábitos de estudo** (horas semanais, tipo de material)
3. **Avalia o perfil cognitivo** (estilo de aprendizagem)
4. **Calcula nível de risco** (baixo, médio, alto)
5. **Gera recomendações personalizadas** baseadas em:
   - Médias baixas → recomendações intensivas
   - Estilo de aprendizagem → tipo de conteúdo sugerido
   - Hábitos de estudo → sugestões de melhoria

**Nota:** Este é um motor simplificado. Para produção, recomenda-se integrar APIs de IA mais avançadas (OpenAI, Google AI, etc.).

## 📝 Estrutura do Banco de Dados

O banco de dados possui as seguintes tabelas principais:

- `users` - Usuários do sistema
- `students` - Dados dos alunos
- `guardians` - Responsáveis
- `teachers` - Professores
- `performance` - Notas e frequência
- `study_habits` - Hábitos de estudo
- `cognitive_profiles` - Perfis cognitivos
- `learning_plans` - Planos de aprendizagem
- `recommendations` - Recomendações dos planos

## 🐛 Solução de Problemas

### Erro de conexão com banco de dados
- Verifique as credenciais em `config/database.php`
- Certifique-se de que o MySQL está rodando
- Verifique se o banco `educare_ai` foi criado

### Página 404 em todas as rotas
- Verifique se o mod_rewrite está habilitado no Apache
- Confirme que o arquivo `.htaccess` está na pasta `public`
- Ajuste a `BASE_URL` em `config/config.php`

### Erro de permissão
- Verifique permissões da pasta `public/uploads`
- No Linux/Mac: `chmod -R 755 public/uploads`

## 📄 Licença

Este projeto foi desenvolvido para fins educacionais.

## 👨‍💻 Desenvolvimento

### Próximas Melhorias Sugeridas

- [ ] Interface para vincular responsáveis a alunos
- [ ] Interface para professores gerenciarem turmas
- [ ] Exportação de relatórios em PDF
- [ ] Gráficos mais avançados
- [ ] Notificações por email
- [ ] Integração com APIs de IA reais
- [ ] Sistema de metas e conquistas
- [ ] Chat/comunicação entre usuários

## 📞 Suporte

Para dúvidas ou problemas, consulte a documentação ou entre em contato com a equipe de desenvolvimento.

---

**Desenvolvido com ❤️ para melhorar a educação através da tecnologia**

