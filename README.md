# 📚 API Acadêmica

API REST para gestão de dados acadêmicos — cadastro de alunos, disciplinas, notas e envio de emails.

---

## 🔗 URL Base

```
{SEU_DOMINIO}/api/v1
```

---

## 📦 Entidades

| Entidade | Descrição |
|----------|-----------|
| 👥 **Alunos** | Cadastro de estudantes (nome, matrícula, email, curso, data de ingresso) |
| 📚 **Disciplinas** | Catálogo de matérias (nome, código, carga horária, professor, semestre) |
| 📊 **Notas** | Avaliações (aluno, disciplina, nota de 0 a 10, período, status) |
| ✉️ **Emails** | Histórico de envios (destinatário, assunto, status) |

---

## 🚀 Endpoints

### 👥 Alunos

| Método | Rota | Descrição |
|--------|------|-----------|
| `GET` | `/alunos` | Listar todos os alunos |
| `GET` | `/alunos/{id}` | Buscar aluno por ID |
| `POST` | `/alunos` | Criar novo aluno |
| `PUT` | `/alunos/{id}` | Atualizar aluno |
| `DELETE` | `/alunos/{id}` | Remover aluno |

**Filtros disponíveis:** `curso`, `page`, `limit`

---

### 📚 Disciplinas

| Método | Rota | Descrição |
|--------|------|-----------|
| `GET` | `/disciplinas` | Listar todas as disciplinas |
| `GET` | `/disciplinas/{id}` | Buscar disciplina por ID |
| `POST` | `/disciplinas` | Criar nova disciplina |
| `PUT` | `/disciplinas/{id}` | Atualizar disciplina |
| `DELETE` | `/disciplinas/{id}` | Remover disciplina |

**Filtros disponíveis:** `semestre`, `page`, `limit`

---

### 📊 Notas

| Método | Rota | Descrição |
|--------|------|-----------|
| `GET` | `/notas` | Listar todas as notas |
| `GET` | `/alunos/{id}/notas` | Notas de um aluno específico |
| `POST` | `/notas` | Lançar nova nota |
| `PUT` | `/notas/{id}` | Atualizar nota |
| `DELETE` | `/notas/{id}` | Remover nota |

**Filtros disponíveis:** `periodo`, `status`, `page`, `limit`

---

### ✉️ Emails

| Método | Rota | Descrição |
|--------|------|-----------|
| `POST` | `/emails/enviar` | Enviar email |
| `GET` | `/emails` | Histórico de emails |

**Filtros disponíveis:** `status`, `page`, `limit`

---

## 💻 Exemplos de Uso

### Python

```python
import requests

BASE = "{SEU_DOMINIO}/api/v1"

# Listar alunos
response = requests.get(f"{BASE}/alunos", params={"curso": "Ciência da Computação"})
alunos = response.json()

# Criar aluno
novo = requests.post(f"{BASE}/alunos", json={
    "nome": "João Santos",
    "matricula": "20250042",
    "email": "joao@faculdade.edu.br",
    "curso": "Engenharia de Software"
}).json()

# Lançar nota
requests.post(f"{BASE}/notas", json={
    "aluno_id": "abc123",
    "disciplina_id": "disc001",
    "valor": 9.0,
    "status": "aprovado"
})

# Enviar email
requests.post(f"{BASE}/emails/enviar", json={
    "destinatario": "maria@faculdade.edu.br",
    "assunto": "Nota disponível",
    "mensagem": "Sua nota de Estrutura de Dados já está disponível."
})
```

### JavaScript

```javascript
const BASE = '{SEU_DOMINIO}/api/v1';

// Listar disciplinas
const response = await fetch(`${BASE}/disciplinas?semestre=2026.1`);
const disciplinas = await response.json();

// Criar disciplina
await fetch(`${BASE}/disciplinas`, {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    nome: 'Inteligência Artificial',
    codigo: 'CC3020',
    carga_horaria: 60,
    professor: 'Dra. Ana Oliveira',
    semestre: '2026.2'
  })
});

// Buscar notas de um aluno
const notas = await fetch(`${BASE}/alunos/abc123/notas`).then(r => r.json());
```

### cURL

```bash
# Listar alunos
curl -X GET "{SEU_DOMINIO}/api/v1/alunos?curso=Ciência+da+Computação"

# Criar aluno
curl -X POST "{SEU_DOMINIO}/api/v1/alunos" \
  -H "Content-Type: application/json" \
  -d '{"nome": "Maria Silva", "matricula": "20240001", "curso": "Ciência de Dados"}'

# Enviar email
curl -X POST "{SEU_DOMINIO}/api/v1/emails/enviar" \
  -H "Content-Type: application/json" \
  -d '{"destinatario": "aluno@faculdade.edu.br", "assunto": "Aviso", "mensagem": "Prova na sexta-feira."}'
```

---

## 🏗️ Stack

- **Frontend:** React + Tailwind CSS + shadcn/ui
- **Backend:** Base44 (BaaS)
- **Banco de Dados:** Gerenciado pelo Base44

---

## 📂 Estrutura do Projeto

```
src/
├── api/           # SDK do Base44
├── components/    # Componentes React (Sidebar, EndpointCard, CodeBlock)
├── entities/      # Schemas das entidades (Aluno, Disciplina, Nota, EmailLog)
├── lib/           # Utilitários, Auth, Query Client
├── pages/         # Páginas (ApiDocs, AdminDashboard)
├── App.jsx        # Rotas principais
├── index.css      # Tema escuro (dark theme)
└── main.jsx       # Entry point
```

---

## 🖥️ Painel Admin

Acesse `/admin` para gerenciar visualmente todos os registros — criar, editar e excluir alunos, disciplinas, notas e enviar emails com registro de histórico.

---
## 📝 Licença
