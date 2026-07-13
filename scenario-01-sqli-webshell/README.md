# Laboratório de Análise de Logs - Simulação de Ataque SQL Injection (SQLi)

## Visão Geral do Cenário
Este laboratório simula um ataque real de Injeção SQL (SQLi) contra uma plataforma de e-commerce fictícia chamada **"LojaVirtual"**. O ambiente é composto por uma aplicação web (Apache/PHP), um firewall de aplicação web (WAF/ModSecurity) e um banco de dados MySQL.

O objetivo deste material é treinar habilidades de correlação de eventos, identificação de falsos positivos, mapeamento da cadeia de ataque (Kill Chain) e elaboração de relatórios executivos com base em evidências técnicas.

---

## Arquivos Disponíveis
| Arquivo | Descrição | Formato |
| :--- | :--- | :--- |
| `waf.log` | Logs do Firewall de Aplicação (ModSecurity) | Data/Hora, Nível, ID da Regra, IP, Ação, Payload |
| `apache.log` | Logs de Acesso do Servidor Web (Apache) | Combined Log Format (IP, Data, Status, User-Agent, Referer) |
| `mysql.log` | Logs de Erro e Consultas do Banco de Dados | Data/Hora, PID, Nível, Cliente, Código do Erro, Query |

---

## Detalhamento do Ataque

### Ator Malicioso
- **IP de Origem:** `200.100.10.50`
- **Ferramenta presumida:** Navegador manual + scripts automatizados (User-Agent: `Mozilla/5.0`)
- **Duração do ataque:** 21 minutos (14:00 às 14:21)

### Vetores Explorados
1. **Parâmetro de Busca (`/busca?q=`):** Testes com `OR`, `UNION SELECT`, `SLEEP()`, `DROP TABLE` e extração de metadados.
2. **Formulário de Login (`POST /login`):** Tentativas de bypass de autenticação (`admin' OR 1=1--`).

### Métricas Técnicas (Dados Corrigidos)
- **Requisições HTTP disparadas pelo atacante:** 16 registros no `apache.log`
- **Alertas críticos gerados no WAF:** 21 registros no `waf.log` (algumas requisições violaram múltiplas regras)
- **Erros gerados no Banco de Dados:** 18 registros no `mysql.log` (as demais requisições foram bloqueadas pelo WAF antes de chegar ao SGBD)

---

## Missão do Analista (Sua Tarefa)

### Fase 1: Correlação Temporal
Utilize os timestamps para casar os eventos. Por exemplo:
- O ataque `livro' OR '1'='1` no WAF (14:00:01) gerou qual erro específico no MySQL? (Resposta: erro #1064)

### Fase 2: Identificação de Falsos Positivos
Nem tudo que parece malicioso é um ataque. Encontre nos logs:
- 1 requisição legítima do Googlebot (User-Agent).
- 1 falso positivo onde o usuário buscava um termo com apóstrofo legítimo (ex: `O'Brien`).
- 1 acesso a um recurso estático (CSS/JS).

### Fase 3: Mapeamento da Cadeia de Ataque (Kill Chain)
Preencha a tabela abaixo com os payloads encontrados:

| Fase | Objetivo | Payload Exemplo (Encontrado no log) |
| :--- | :--- | :--- |
| **Reconhecimento** | Testar se a aplicação aceita comandos SQL | ? |
| **Fingerprinting** | Descobrir versão do DB e nome do schema | ? |
| **Exfiltração** | Roubar credenciais da tabela `users` | ? |
| **Destruição/DoS** | Tentar apagar dados ou causar timeout | ? |

### Fase 4: Relatório Executivo
Com base na análise, responda:
- O WAF bloqueou 100% dos ataques? Houve algum status `200` (sucesso) para payloads maliciosos?
- O atacante conseguiu extrair algum dado sensível? Justifique com os códigos de status HTTP.
- Qual ação defensiva imediata você tomaria (além de bloquear o IP)?

---

## Como Utilizar este Laboratório

1. Crie uma pasta chamada `logs-sqli-lab`.
2. Copie o conteúdo dos 3 blocos de código abaixo (WAF, Apache, MySQL) e salve cada um em seu respectivo arquivo (`.log`).
3. Abra os arquivos em um editor de texto com syntax highlight (ex: VS Code, Notepad++).
4. Utilize ferramentas como `grep`, `awk` ou planilhas (Excel/Google Sheets) para filtrar e ordenar os eventos.
5. Documente suas descobertas em um relatório final (DOCX/PDF).

---

## Resolução / Gabarito (Para Instrutores)
*[Escondido - Instrutores podem solicitar ao autor]*

---

**Boa análise! Lembre-se: em segurança, a correlação de eventos é tão importante quanto a tecnologia empregada.**
