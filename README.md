# Portfólio de Análise de Logs de Segurança

Este repositório contém cenários simulados de incidentes cibernéticos, analisados **manualmente**, sem uso de SIEM, scripts ou ferramentas automatizadas. O objetivo é demonstrar capacidade de leitura, correlação e investigação de logs de múltiplas fontes.

## Cenários

| # | Cenário | Dificuldade | Técnicas |
|---|---------|------------|----------|
| 1 | [SQL Injection → Webshell → Reverse Shell](./scenario-01-sqli-webshell/) | Iniciante-Intermediário | SQLi, upload de webshell, execução de comandos, reverse shell, escalação via sudo |
| 2 | [Apache Struts RCE → Cobalt Strike Beacon](./scenario-02-struts-rce/) | Intermediário | OGNL injection, webshell JSP, Cobalt Strike beacon, movimento lateral (SMB), DC pwn |
| 3 | [WordPress Theme Upload → socat Reverse Shell](./scenario-03-wordpress-theme-upload/) | Intermediário | WP admin takeover, upload de tema malicioso, socat reverse shell, pass-the-hash, DCSync |
| 4 | [Node.js Command Injection → Pass-the-Hash](./scenario-04-nodejs-command-injection/) | Intermediário-Avançado | Command injection, reverse shell Bash, pass-the-hash, Kerberoasting, exfiltração DNS |
| 5 | [Kerberoasting, DCSync & Cloud Exfil](./scenario-05-kerberoasting-dcsync/) | Avançado | Pickle deserialization, beacon HTTPS, Kerberoasting, DCSync, exfiltração S3/DNS |

Cada subpasta contém os **logs brutos** e um arquivo `analysis.md` o qual ainda está em desenvolvimento **Resumo Executivo**.

## Habilidades demonstradas

- Leitura de logs de firewall (iptables), servidores web (Apache, Flask), sistemas operacionais (Linux auth.log, Windows Security), dispositivos de rede (Cisco IOS) e IDS (Snort).
- Identificação de padrões de ataque: varredura, força bruta, injeção de código, ofuscação (Base64, URL-encode), reverse shells, tunelamento DNS, pass‑the‑hash, Kerberoasting, DCSync.
- Correlação temporal entre eventos de múltiplas fontes.
- Diferenciação entre tráfego malicioso, legítimo e scanners autorizados (Nessus).
- Documentação de timelines, IOCs e lições aprendidas.

## Sobre mim

Sou um profissional de tecnologia com foco em cibersegurança, infraestrutura e desenvolvimento de software. Tenho grande interesse em compreender o funcionamento interno dos sistemas, analisar vulnerabilidades e encontrar soluções para problemas complexos, sempre buscando entender o "como" e o "porquê" das tecnologias.

Minha principal área de interesse é a segurança ofensiva (Red Team/Pentest), aliada à análise de redes, sistemas Linux e Windows, engenharia reversa, forense digital e automação de tarefas. Também possuo experiência com desenvolvimento de aplicações, o que me permite compreender tanto a perspectiva de quem constrói sistemas quanto a de quem os avalia em busca de falhas.

Acredito que a melhor forma de aprender é colocando a mão na massa. Por isso, utilizo este repositório para documentar estudos, laboratórios, desafios CTF, pesquisas, scripts e projetos relacionados à segurança da informação. Meu objetivo é construir conhecimento de forma contínua e compartilhar minha evolução técnica ao longo da jornada.

Estou sempre em busca de novos desafios que me permitam expandir minhas habilidades e aprofundar meus conhecimentos em cibersegurança, redes, sistemas operacionais e desenvolvimento.

## Contato

LinkedIn - https://www.linkedin.com/in/mihael-maciel-zottis/
Email - mihaelmaciel@gmail.com
