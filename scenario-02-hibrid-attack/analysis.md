# RELATÓRIO DE INCIDENTE DE SEGURANÇA - OPERAÇÃO FANTASMA
**Nº do Incidente:** INC-2026-07-15-001  
**Data do Incidente:** 15/07/2026  
**Hora do Incidente:** 09:00:12 às 09:21:00 (UTC-3)  
**Sistema Afetado:** Plataforma de E-commerce (LojaVirtual) + Servidor Backend (SSH)  
**Classificação:** Tentativa de Ataque Multivetor (SQLi, XSS, LFI, Brute Force, RCE)  
**Status:** CONTIDO (sem vazamento ou indisponibilidade)

##Resumo Executivo##
No dia 15/07/2026, entre 09:00 e 09:21, nossa equipe identificou um ataque coordenado contra a plataforma de e-commerce, envolvendo três IPs externos e um IP interno comprometido.
Foam empregadas técnicas de Path Traversal (LFI), Cross-Site Scripting (XSS), SQL Injection, Força Bruta e tentativa de upload de Web Shell. Graças à atuação do WAF e dos controles de acesso, **todas as tentativas foarm bloqueadas** (status HTTP 403), e não houve acesso indevido a dados ou sistemas. O IP interno (10.0.0.5) foi isolado para investigação de possível movimentação lateral. O incidente é considerado **CONTIDO**.

##Linha do Tempo do Incidente##
 |  Horário  |  Evento  |  Atacante  |  Detalhes  | 
 | :--- | :--- | :--- | :--- |
 | 09:00:12 | Início do ataque | 185.220.101.23 | Primeira tentativa de LFI (/etc/passwd) | 
 | 09:00:20 | Início do ataque SSH | 10.0.0.5 (interno) | Força bruta contra SSH | 
 | 09:02:10 | Primeira tentativa SQLi | 200.100.10.50 | Payload ' OR '1'='1 | 
 | 09:06:30 | Primeira tentativa XSS | 45.33.22.11 | Payload <script>alert('XSS')</script> | 
 | 09:07:00 | Tentativa de SQLi no login | 45.33.22.11 | admin' OR 'x'='x | 
 | 09:10:15 | Tentativa de upload de shell | 185.220.101.23 | shell.php | 
 | 09:13:00 - 09:15:30 | Força Bruta no /admin | 45.33.22.11 | 5 tentativas com senhas comuns | 
 | 09:21:00	Último evento | 200.100.10.50 | Time-Based Blind SQLi (SLEEP) | 
