# default_template

Vzorové GitHub template repository pro nové projekty v organizaci **Good-Gear-Universe**. Obsahuje předkonfigurovaná pravidla pro Cursor AI, doporučený Git workflow a bezpečnostní konvence.

> Tento repozitář slouží jako výchozí bod — neobsahuje aplikační kód. Po vytvoření nového projektu z template doplňte sekce níže podle konkrétního projektu.

---

## Obsah

- [Použití template](#použití-template)
- [Co je součástí](#co-je-součástí)
- [Cursor pravidla](#cursor-pravidla)
- [Git a Linear workflow](#git-a-linear-workflow)
- [Doporučený tech stack](#doporučený-tech-stack)
- [Bezpečnost](#bezpečnost)
- [Bootstrap nového projektu](#bootstrap-nového-projektu)
- [Kontrolní seznam po vytvoření projektu](#kontrolní-seznam-po-vytvoření-projektu)

---

## Použití template

### Vytvoření nového repozitáře z template

1. Na GitHubu otevřete [default_template](https://github.com/Good-Gear-Universe/default_template).
2. Klikněte na **Use this template** → **Create a new repository**.
3. Zadejte název nového repozitáře a vyberte viditelnost.
4. Po vytvoření naklonujte repozitář lokálně:

```bash
git clone https://github.com/Good-Gear-Universe/<nazev-noveho-repo>.git
cd <nazev-noveho-repo>
```

### Lokální vývoj

Po bootstrapu aplikace (viz [Bootstrap nového projektu](#bootstrap-nového-projektu)) typicky spustíte:

```bash
npm install
cp .env.example .env.local   # doplňte hodnoty
npm run dev
```

---

## Co je součástí

| Položka | Popis |
|---------|-------|
| `.cursor/rules/` | Pravidla pro Cursor AI agenta — workflow, kódování, bezpečnost |
| `README.md` | Tento soubor — vzorová dokumentace projektu |

---

## Cursor pravidla

Pravidla v `.cursor/rules/` se automaticky aplikují při práci s Cursor AI v tomto repozitáři.

### `git-workflow.mdc`

Definuje spolupráci s GitHubem a Linear:

- Každý úkol by měl být navázán na Linear issue (pokud existuje).
- Pojmenování větví: `feature/LIN-123-kratky-popis`, `fix/...`, `chore/...`, `docs/...`
- Commit zprávy podle [Conventional Commits](https://www.conventionalcommits.org/).
- Pull requesty místo přímých commitů do `main`.

### `project-rules.mdc`

Pravidla pro vývoj aplikace:

- Prozkoumat existující kód před úpravami.
- Nevymýšlet API, env proměnné, DB sloupce ani routy.
- Malé, bezpečné a udržovatelné změny.
- TypeScript se striktním typováním.
- Respektovat konvence Next.js, Prisma a Supabase.
- Po změnách spouštět relevantní kontroly (`lint`, `typecheck`, `test`, `build`).

### `security.mdc`

Bezpečnostní pravidla:

- Nikdy necommitovat secrets (`.env`, klíče, certifikáty).
- Používat `.env.example` pouze pro dokumentaci.
- Validovat env proměnné před použitím.
- Vyžadovat schválení pro rizikové operace (migrace, deploy, push, změny auth).

---

## Git a Linear workflow

### Pojmenování větví

```
feature/LIN-123-kratky-popis
fix/LIN-456-oprava-chyby
chore/LIN-789-aktualizace-zavislosti
docs/LIN-101-aktualizace-readme
```

### Commit zprávy (Conventional Commits)

```
feat: add attendance join flow
fix: correct Prisma client initialization
chore: update CI workflow
docs: update deployment guide
```

### Pull request

**Titulek:** stejná konvence jako commit zprávy.

**Tělo PR musí obsahovat:**

- **Summary** — stručný popis změny
- **Changes** — co konkrétně bylo upraveno
- **Tests performed** — jak bylo otestováno
- **Linked issue:** `Closes LIN-123`

**Pravidla:**

- Nemergovat přímo do `main`.
- Preferovat pull requesty před přímými commity do `main`.

---

## Doporučený tech stack

Template předpokládá full-stack projekt s těmito technologiemi (upravte podle potřeby v novém repozitáři):

| Vrstva | Technologie |
|--------|-------------|
| Frontend / API | Next.js (App Router, Server/Client Components) |
| Databáze | Prisma ORM |
| Backend služby | Supabase |
| Infrastruktura | Cloudflare (Workers, Pages) |
| Issue tracking | Linear |
| Version control | GitHub |

---

## Bezpečnost

- Secrets pouze v `.env.local` nebo v CI/CD secrets — nikdy v repozitáři.
- Supabase **service role key** nikdy na klientovi.
- Pro Cloudflare, GitHub, Linear, Supabase a Google Cloud používat tokeny s minimálními oprávněními.
- Destruktivní operace (migrace, deploy, mazání souborů) vyžadují explicitní schválení.

---

## Bootstrap nového projektu

Po vytvoření repozitáře z template doporučené kroky:

1. **Upravit README** — nahradit placeholder sekce názvem projektu, popisem a instrukcemi ke spuštění.
2. **Inicializovat aplikaci** — např. `npx create-next-app@latest .` nebo jiný framework dle potřeby.
3. **Přidat `.env.example`** — zdokumentovat všechny potřebné env proměnné bez skutečných hodnot.
4. **Nastavit CI** — GitHub Actions pro lint, typecheck, test a build.
5. **Propojit Linear** — nastavit integraci s GitHubem pro automatické linkování issue.
6. **Nastavit branch protection** — na `main` vyžadovat PR review a passing checks.

---

## Kontrolní seznam po vytvoření projektu

- [ ] README upraveno pro konkrétní projekt
- [ ] Aplikace inicializována a běží lokálně
- [ ] `.env.example` vytvořen, `.env.local` v `.gitignore`
- [ ] CI pipeline nastavena a prochází
- [ ] Branch protection na `main` aktivní
- [ ] Linear projekt propojen s repozitářem
- [ ] Cursor pravidla zkontrolována a případně rozšířena

---

## Licence

Doplňte licenci podle potřeby projektu (např. MIT, proprietární).

## Kontakt

Doplňte kontroli / tým zodpovědný za projekt.
