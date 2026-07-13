# Análise do Cenário 1

**Data da análise:** 20/05/2026

## 1. Resultado da Análise de Incidente (Simulação SQLi)
**Data do Evento: 30/Jun/2026**
**Duração do Ataque: 21 minutos (14:00 às 14:21)**
**Sistema Afetado: Plataforma de E-commerce**

## 2. Cenário Geral
Foi identificada uma tentativa ativa de Injeção de Código SQL (SQLi) contra nossa aplicação web, originada do endereço de IP 203.100.10.50. Foram feitos no total 21 requisições maliciosas, visando dois alvos críticos: a busca de produtos (/busca) e a autenticação de usuários (/login).

## 3. Fases do Ataque
- **Fase 1 - Teste de Viabilidade:** Uso de payloads booleanos simples. O objetivo era verificar se o sistema interpretava entradas do usuário como comandos SQL. Se tivesse funcionado, ele teria acesso a todos produtos e dados do banco em segundos.
- **Fase 2 - Fingerprint:** Extração de metadados do servidor (@@version, database()). O atacante mapeou a tecnologia e a estrutura do nosso banco de dados para preparar ataques mais pesados.
- **Fase 3 - Exfiltração e Destruição:** Tentativa de roubo direto de credenciais (password FROM users) e execução de comandos destrutivos no sistema operacional (xp_cmdshell para apagar arquivos).


