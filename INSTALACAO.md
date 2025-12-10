# Guia Rápido de Instalação - Educare.AI

## ⚡ Instalação Rápida (5 minutos)

### 1. Banco de Dados
```sql
-- Execute no phpMyAdmin ou MySQL
source sql/schema.sql
```

### 2. Configuração
Edite `config/database.php`:
```php
private const HOST = 'localhost';
private const DB_NAME = 'educare_ai';
private const USERNAME = 'root';
private const PASSWORD = '';  // Sua senha MySQL
```

Edite `config/config.php`:
```php
define('BASE_URL', 'http://localhost/educare/public');
```

### 3. Acesse
Abra no navegador: `http://localhost/educare/public`

## 🧪 Teste Rápido

1. **Cadastre um aluno:**
   - Acesse: `http://localhost/educare/public/auth/register`
   - Tipo: Aluno
   - Preencha os dados

2. **Cadastre um professor:**
   - Faça logout
   - Cadastre como Professor
   - Disciplina: Matemática

3. **Vincule aluno ao professor (via SQL):**
```sql
-- Primeiro, descubra os IDs
SELECT id, user_id FROM students;
SELECT id, user_id FROM teachers;

-- Depois, vincule (substitua os IDs)
INSERT INTO teacher_student (teacher_id, student_id, disciplina) 
VALUES (1, 1, 'Matemática');
```

4. **Faça login como aluno:**
   - Cadastre hábitos de estudo
   - Preencha perfil cognitivo

5. **Faça login como professor:**
   - Cadastre algumas notas para o aluno

6. **Volte como aluno:**
   - Gere um plano de aprendizagem
   - Veja as recomendações!

## ✅ Checklist

- [ ] MySQL rodando
- [ ] Banco `educare_ai` criado
- [ ] Tabelas importadas (schema.sql)
- [ ] Configurações ajustadas (database.php, config.php)
- [ ] Pasta `public/uploads` com permissão de escrita
- [ ] mod_rewrite habilitado (Apache)

## 🐛 Problemas Comuns

**Erro 500:**
- Verifique se o MySQL está rodando
- Verifique as credenciais em `config/database.php`

**Página em branco:**
- Ative exibição de erros em `config/config.php` (ENVIRONMENT = 'development')
- Verifique logs do PHP

**404 em todas as rotas:**
- Verifique se `.htaccess` está na pasta `public`
- Verifique se mod_rewrite está habilitado
- Ajuste `BASE_URL` em `config/config.php`

