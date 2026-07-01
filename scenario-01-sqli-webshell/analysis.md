# Análise do Cenário 1

**Data da análise:** 20/05/2026

## 1. Resumo executivo


## 2. Linha do tempo
| Horário (UTC) | Fonte | Evento |
|---------------|-------|--------|
| 08:00:10 | Firewall | SYN scan de 203.0.113.200 nas portas 80/443 |
| 08:00:13 | Apache | SQLi test (`' OR '1'='1`) |
| ... | ... | ... |

## 3. Classificação de IPs
- **Atacante 1:** 203.0.113.200
- **Atacante 2:** 203.0.113.201
- **Scanner autorizado:** (nenhum)
- **Host comprometido:** 172.16.10.5
- **Movimento lateral:** 172.16.50.10

## 4. IOCs
- IPs: 203.0.113.200, 203.0.113.201, 198.51.100.80
- Hashes/credenciais:
- Arquivos: /tmp/nc, shell.php

## 5. Lições aprendidas
- Necessidade de validação de entradas (SQLi)
- Restringir permissões sudo (www-data → root)
- Monitorar upload de arquivos PHP
