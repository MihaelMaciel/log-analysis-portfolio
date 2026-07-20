## Resumo ##
Nossa equipe investigou inumeros alertas de uma tentativa de SQLi agressiva e ao investigar mais a fundo o incidente notamos que aparentemente não houve danos pois a higienização, firewall e outros meios de controle estavam bem configurados assim evitando que o intruso obtivesse sucesso.

## Evidencias ##
Foram identificados 14 alertas de SQLi atráves dos registros do Apache.log, 21 do firewall.log e 19 do server.log.

## Análise Técnica ##
O atacante começou com escaneando o que ele poderia fazer, iniciou com SQLi básico OR 1 = 1, após isso tentou capturar metadados e após isso começou a ser mais agressivo ao tentar derrubar o DB.
