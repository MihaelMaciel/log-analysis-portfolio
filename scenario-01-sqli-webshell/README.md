# Cenário 1 – SQL Injection, Webshell e Reverse Shell

**Rede:** 172.16.0.0/16  
**Servidor Web:** 172.16.10.5 (Apache/PHP)  
**Controlador de Domínio:** 172.16.10.200 (Windows)  
**Data do incidente:** 15 de junho de 2026, 08:00–09:30 UTC

## Resumo

Um atacante externo (203.0.113.200) realizou varredura de portas, explorou uma injeção SQL no parâmetro `id` de `produtos.php`, obteve acesso ao painel administrativo, fez upload de um webshell PHP e executou comandos como root (via sudo mal configurado). Em seguida, baixou o netcat e estabeleceu um reverse shell para 198.51.100.80:4444. Um segundo atacante (203.0.113.201) explorou path traversal para ler `/etc/shadow`. O host interno 172.16.50.10 realizou movimento lateral via SSH e SMB, culminando na adição do usuário `eviluser` ao grupo Domain Admins.

## Técnicas identificadas

- Reconhecimento: SYN scans nas portas 80, 443, 22, 8080, 3306
- Exploração: SQL Injection (manual e com sqlmap), path traversal (LFI)
- Pós-exploração: Webshell, execução de comandos (`cat /etc/passwd`, `wget`, `nc -e /bin/sh`)
- Movimento lateral: Força bruta SSH, pass-the-hash (SMB)
- Persistência: Criação de usuário no grupo Domain Admins

## Arquivos de log

- `firewall.log` – iptables
- `apache.log` – Apache access log
- `auth-linux.log` – auth.log do servidor web
- `security-windows.log` – Security log do DC
- `cisco.log` – Syslog de switch/roteador Cisco
- `snort-alerts.log` – Alertas de IDS

## Análise completa

Veja o arquivo [`analysis.md`](./analysis.md).
