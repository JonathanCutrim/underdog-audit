# underdog-audit

Registro público de auditoria dos sinais da **Underdog Tips**.

Cada linha de `chain.log` é `seq|timestamp|hash` — o **hash** de um sinal, publicado no
instante do disparo, **antes do jogo**. O hash não revela o palpite (commit-reveal): o pick
só é revelado depois que o jogo acaba, na página de auditoria.

O que isso prova: como o commit tem o **carimbo de tempo do GitHub** (que a Underdog não
controla), dá pra confirmar que o sinal existia **antes da bola rolar** — sem precisar
confiar na palavra de ninguém.

Como conferir: pegue um sinal liquidado na página de auditoria, monte o texto
`seq|ts|event_id|market|side|pick|odd|signal|game_time|nonce|prev_hash`, calcule o SHA-256 e
compare com o `hash` desta linha. Se bater, e o commit for anterior ao horário do jogo, está provado.

Página: https://underdog.tips/audit
