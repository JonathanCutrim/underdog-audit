# underdog-audit

Registro público de auditoria dos sinais da **Underdog Tips** (tênis de mesa).

Cada sinal vira **um commit** neste repositório, com uma linha em [`chain.log`](chain.log):

```
seq | timestamp (unix) | hash
```

O **hash** é publicado no instante do disparo — **antes do jogo**. O hash não revela o palpite
(esquema *commit-reveal*): o pick só aparece depois que o jogo acaba, na página de auditoria.

## O que isto prova — e o que NÃO prova (sendo honesto)

**Prova:** que aquele hash existia num commit público **antes** do jogo começar. Como o histórico é
aberto, dá pra confirmar que a previsão foi feita antes do resultado — sem confiar na palavra da Underdog.

**Os limites, com honestidade:** este é um repositório que a Underdog controla. A *data* de um commit
git, sozinha, pode ser manipulada, e um `force-push` é tecnicamente possível. O que protege contra isso:
o histórico é **público**, o GitHub registra quando **recebeu** cada push, e qualquer um pode **clonar
e espelhar** o repo — então qualquer reescrita fica visível. **Não é prova matemática absoluta; é
transparência pública, aberta pra qualquer um auditar e denunciar.**

## Como conferir um sinal (passo a passo)

1. Pegue um sinal **finalizado** em https://underdog.tips/audit — toque nele (copia o hash) ou use o
   botão **Conferir**.
2. A página mostra o **payload** (o texto exato) e o **hash**. Confira que `SHA-256(payload)` = o hash.
   No terminal: `printf '%s' 'COLE_O_PAYLOAD' | sha256sum`
3. Procure esse hash aqui no [`chain.log`](chain.log) e abra o **commit** dele (aba *Commits* do GitHub,
   ou `git log`). O horário do commit tem que ser **anterior** ao horário do jogo (que a página mostra).
4. Bateu o hash **e** o commit veio antes do jogo? Provado.

## Espelhe você mesmo

Quer garantia extra? Guarde uma cópia: `git clone https://github.com/JonathanCutrim/underdog-audit`.
Se algum dia o histórico for reescrito, a sua cópia denuncia.

---
Página de auditoria: **https://underdog.tips/audit**
