# Cenário 2 – Apache Struts RCE, Cobalt Strike & Movimento Lateral

**Rede:** 10.10.0.0/16  
**Servidor Web:** 10.10.5.10 (Apache Tomcat/Struts2)  
**Controlador de Domínio:** 10.10.10.10 (Windows)  
**Data:** 19 de junho de 2026, 09:00–11:00 UTC

## Resumo

Atacante externo (198.51.100.150) explorou uma vulnerabilidade de OGNL injection no Struts2 (CVE-2017-5638) via `/struts2-showcase/`. Após upload de webshell JSP, baixou um beacon Cobalt Strike, estabeleceu comunicação HTTPS reversa, moveu-se lateralmente usando pass-the-hash contra o DC e adicionou o usuário `svc_apache` ao grupo sudo e `svc_backup` ao Domain Admins. Um scanner interno autorizado (Nessus, 10.10.1.200) gerou ruído.

## Técnicas

- Reconhecimento: scan na porta 8443, brute force SSH
- Exploração: Apache Struts OGNL injection
- Pós-exploração: Webshell JSP, download de beacon Cobalt Strike
- C2: Beacon HTTPS periódico (120s)
- Movimento lateral: SMB pass-the-hash, criação de conta privilegiada
- Exfiltração: túnel DNS

## Arquivos

- `firewall.log`
- `apache.log`
- `auth-linux.log`
- `security-windows.log`
- `cisco.log`
- `snort-alerts.log`

## Análise completa

Veja [`analysis.md`](./analysis.md).
