# AulaSempre

Plataforma web B2B para escolas encontrarem rapidamente **professores substitutos** qualificados e disponíveis.

## Estrutura

```
AulaSempre/
├── aulasempre.sql   ← Schema oficial MySQL (DDL + DML + DQL)
├── backend/         ← API REST em Spring Boot 3 + Java 21
├── frontend/        ← SPA Angular 22 + Angular Material
├── CHANGELOG.md     ← Histórico de alterações por incremento
└── README.md
```

## Stack

| Camada     | Tecnologia                               |
|------------|------------------------------------------|
| Frontend   | Angular 22 + Angular Material            |
| Backend    | Spring Boot 3.4 + Spring Security + JWT  |
| Banco      | H2 (dev) / MySQL 8 (produção)           |
| Comunicação| API REST / JSON                          |

## Requisitos

- Java 21+
- Node.js 22+ (necessário para o Angular CLI 22)
- MySQL 8 (para rodar com profile `mysql`)
- Não é preciso instalar Maven: o `mvnw`/`mvnw.cmd` baixa tudo sozinho

## Como Rodar

### Backend (H2 — padrão, sem instalar nada)
```powershell
cd backend
.\mvnw.cmd spring-boot:run
```
- API: http://localhost:8080
- Console H2: http://localhost:8080/h2-console

### Backend (MySQL — requer MySQL rodando + schema importado)
```powershell
cd backend
.\mvnw.cmd spring-boot:run -Dspring-boot.run.profiles=mysql
```

### Frontend
```powershell
cd frontend
npm install
ng serve
```
- App: http://localhost:4200

## Schema do Banco

O arquivo `aulasempre.sql` contém a estrutura completa:
- **DDL:** 11 tabelas (escola, usuario, professor, formacao, disciplina, professor_disciplina, nivel_ensino, professor_nivel_ensino, disponibilidade, solicitacao_substituicao, convite, substituicao, avaliacao)
- **DML:** Dados fictícios de teste (3 escolas, 8 usuários, 5 professores com formações, disciplinas, disponibilidades, solicitações e convites)
- **DQL:** 12 consultas analíticas e de integração

### Credenciais de teste (DML)
- **Senha:** `senha123` (todos os usuários)

## Fluxo Principal

```
Escola → cria solicitação → sistema encontra professores compatíveis
→ escola consulta perfil → envia convite → professor aceita/recusa
→ substituição registrada → avaliação
```

## Status do Desenvolvimento

O projeto está sendo construído incrementalmente. Veja o [CHANGELOG.md](CHANGELOG.md) para o histórico detalhado.
