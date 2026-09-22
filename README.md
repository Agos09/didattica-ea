# Appunti di Economia Aziendale

Sito pubblico: **https://didattica.wealth.finance** (Workers `didattica-ea`; fallback `*.workers.dev`).

**Questa repo non è la SSoT.** Il fascicolo completo (programmazioni, verbali, journal) sta su Forgejo: `agostino/scuola` (`~/Code/scuola`). Qui arriva solo `didattica/` più la config di build/deploy.

## Workflow

1. Modifica gli `.adoc` in `~/Code/scuola/didattica/`.
2. Commit e push su Hetzner (`git push hetzner`).
3. Esporta lo slice pubblico:

```bash
cd ~/Code/scuola
make github-sync
```

4. Il push su `origin` (`Agos09/didattica-ea`) scatena GitHub Actions → `npm run build` → `wrangler deploy`.

Non fare `git pull` da GitHub verso `~/Code/scuola`.

## Locale

```bash
npm ci
npm run build          # output in ./public (gitignored)
npx wrangler deploy    # richiede wrangler login
```

## Secrets GitHub

- `CLOUDFLARE_API_TOKEN` — token API con permesso Workers
- `CLOUDFLARE_ACCOUNT_ID` — `fd5849baedd7bf3df62037186c87e4b3`
