# 📚 Como Funciona o Cadastro de Alunos - Educare.AI

## 📋 Resumo

O sistema Educare.AI oferece **duas formas** de cadastrar alunos:

1. **Auto-cadastro** - O próprio aluno se cadastra
2. **Cadastro por Professor** - Professores cadastram alunos no sistema

---

## 🔐 1. Auto-Cadastro (Cadastro Público)

### Quem pode fazer:
- **Qualquer pessoa** pode se cadastrar como aluno através da página pública de registro

### Como funciona:
1. Acesse: `http://localhost:8080/educare/public/auth/register`
2. Preencha os dados:
   - Nome completo
   - Email
   - Senha (mínimo 6 caracteres)
   - Tipo de usuário: **Aluno**
   - Dados escolares (opcional):
     - Escola
     - Série
     - Turma
3. Clique em "Criar Conta"
4. Faça login com as credenciais criadas

### Vantagens:
- ✅ Processo rápido e simples
- ✅ Aluno cria sua própria conta
- ✅ Não requer intervenção de terceiros

### Desvantagens:
- ⚠️ Não há controle sobre quem se cadastra
- ⚠️ Aluno pode não preencher dados corretos
- ⚠️ Não há vínculo automático com professores

---

## 👨‍🏫 2. Cadastro por Professor (Recomendado)

### Quem pode fazer:
- **Apenas professores** autenticados no sistema

### Como funciona:
1. **Faça login como professor**
2. No menu, clique em **"Gerenciar Alunos"**
3. Clique em **"Cadastrar Novo Aluno"**
4. Preencha os dados do aluno:
   
   **Dados de Acesso:**
   - Nome completo *
   - Email *
   - Senha * (mínimo 6 caracteres)
   - Data de nascimento
   
   **Dados Escolares:**
   - Escola
   - Série
   - Turma
   
   **Contato:**
   - Telefone
   - Endereço
   
   **Vínculo:**
   - ☑️ Vincular este aluno à minha turma (opcional)
   - Disciplina (se marcar o vínculo)

5. Clique em **"Cadastrar Aluno"**

### Vantagens:
- ✅ Controle total sobre o cadastro
- ✅ Dados mais completos e confiáveis
- ✅ Vínculo automático com o professor
- ✅ Professor pode editar dados posteriormente
- ✅ Melhor organização para escolas

### Funcionalidades Adicionais:
- **Listar todos os alunos** cadastrados
- **Editar dados** de alunos existentes
- **Cadastrar notas** diretamente da lista
- **Vincular alunos** à turma do professor

---

## 🔗 Vínculo Professor-Aluno

### Como vincular:
1. **Durante o cadastro:**
   - Marque a opção "Vincular este aluno à minha turma"
   - O sistema vincula automaticamente

2. **Manual (via SQL):**
   ```sql
   INSERT INTO teacher_student (teacher_id, student_id, disciplina) 
   VALUES (1, 1, 'Matemática');
   ```

### Importância do vínculo:
- Permite que o professor veja o aluno no dashboard
- Permite cadastrar notas para o aluno
- Permite visualizar planos de aprendizagem do aluno

---

## 📊 Comparação dos Métodos

| Característica | Auto-Cadastro | Cadastro por Professor |
|----------------|---------------|------------------------|
| **Controle** | Baixo | Alto |
| **Dados completos** | Depende do aluno | Garantido |
| **Vínculo automático** | Não | Sim (opcional) |
| **Edição posterior** | Apenas pelo aluno | Pelo professor |
| **Ideal para** | Testes, uso pessoal | Ambiente escolar |

---

## 🎯 Recomendação de Uso

### Para Ambiente Escolar Real:
✅ **Use o cadastro por professor** para:
- Garantir dados corretos
- Manter controle sobre os alunos
- Facilitar a gestão da turma
- Organizar melhor o sistema

### Para Testes/Desenvolvimento:
✅ **Use o auto-cadastro** para:
- Testar funcionalidades rapidamente
- Criar contas de teste
- Desenvolvimento e demonstrações

---

## 🔧 Funcionalidades do Módulo de Gestão de Alunos

### Para Professores:

1. **Listar Alunos** (`/students`)
   - Ver todos os alunos cadastrados
   - Visualizar dados básicos (nome, email, escola, série, turma)
   - Acesso rápido para editar ou cadastrar notas

2. **Cadastrar Aluno** (`/students/cadastrar`)
   - Formulário completo com todos os dados
   - Opção de vincular à turma do professor
   - Validação de email único

3. **Editar Aluno** (`/students/editar/{id}`)
   - Atualizar dados escolares
   - Atualizar dados de contato
   - Atualizar nome e email

4. **Cadastrar Notas** (da lista de alunos)
   - Botão rápido para cadastrar notas
   - Já pré-seleciona o aluno

---

## 📝 Exemplo de Fluxo Completo

### Cenário: Professor cadastra aluno e começa a usar o sistema

1. **Professor faz login**
   - Acessa o dashboard

2. **Cadastra aluno**
   - Menu → "Gerenciar Alunos"
   - "Cadastrar Novo Aluno"
   - Preenche dados completos
   - Marca "Vincular à minha turma"
   - Salva

3. **Aluno recebe credenciais**
   - Professor informa email e senha ao aluno
   - Aluno faz login

4. **Aluno completa perfil**
   - Cadastra hábitos de estudo
   - Preenche perfil cognitivo

5. **Professor cadastra notas**
   - Menu → "Cadastrar Notas"
   - Seleciona o aluno
   - Cadastra avaliações

6. **Sistema gera plano**
   - Aluno gera plano de aprendizagem
   - Sistema cria recomendações personalizadas

---

## ⚠️ Observações Importantes

1. **Email único:** Cada email só pode ser usado uma vez no sistema
2. **Senha:** Mínimo de 6 caracteres (recomendado: 8+ com letras e números)
3. **Vínculo:** Alunos podem estar vinculados a múltiplos professores
4. **Edição:** Professores podem editar dados escolares, mas não a senha do aluno
5. **Segurança:** Senhas são armazenadas com hash (bcrypt) - não podem ser recuperadas

---

## 🚀 Próximas Melhorias Sugeridas

- [ ] Envio de email com credenciais ao cadastrar aluno
- [ ] Recuperação de senha
- [ ] Importação em massa (CSV/Excel)
- [ ] Perfil de administrador para gestão completa
- [ ] Histórico de alterações nos dados do aluno

---

**Desenvolvido para facilitar a gestão educacional! 🎓**

