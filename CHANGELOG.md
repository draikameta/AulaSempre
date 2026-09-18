# Changelog — AulaSempre

Todas as alterações relevantes do projeto são documentadas neste arquivo.
Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/).

---

## [Incremento 1] — 2026-09-18

### Adicionado
- `backend/src/main/resources/application-mysql.properties` — Profile Spring Boot dedicado ao MySQL com `ddl-auto=validate` (schema controlado pelo `aulasempre.sql`).
- `CHANGELOG.md` — Arquivo de histórico de alterações por incremento.
- `aulasempre.sql` — Script SQL oficial do projeto (DDL + DML + DQL) adicionado ao repositório.

### Alterado
- `backend/src/main/resources/application.properties` — Limpeza: removida seção MySQL comentada (agora vive no profile `application-mysql.properties`); adicionada instrução de ativação do profile MySQL no cabeçalho.
- `aulasempre.sql` — Hashes de senha dos 8 usuários de teste atualizados para o hash BCrypt verificado de `senha123` (`$2b$10$Wyf.POt...`), compatível com Spring Security.
- `README.md` — Reescrito para refletir o estado real do repositório, com instruções de execução para ambos os profiles (H2 e MySQL).

### Notas técnicas
- **Profile H2 (padrão):** `./mvnw spring-boot:run` — banco em memória, sem instalar nada.
- **Profile MySQL:** `./mvnw spring-boot:run -Dspring-boot.run.profiles=mysql` — requer MySQL rodando com o schema importado via `aulasempre.sql`.
- O Hibernate **não** gerencia o schema quando conectado ao MySQL (`ddl-auto=validate`). Todo DDL é controlado pelo script SQL.
