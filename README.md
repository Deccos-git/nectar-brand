# nectar-brand

De **enige bron** voor de Nectar-huisstijl: design tokens (`tokens.css`) en de
gerenderde style guide (`styleguide.html`). Website en app trekken dit binnen als
dependency — er staan **geen gekopieerde tokenwaarden** in de productrepo's.

> **Regel:** bewerk `tokens.css` en `styleguide.html` **alleen hier**. Elke kleur,
> font en spacing in website/app verwijst naar een CSS-variabele (`var(--...)`),
> nooit naar een losse hexwaarde.

## Installeren (website & app)

Met de package manager die de repo al gebruikt (hier: npm):

```bash
npm install github:Deccos-git/nectar-brand#main
```

Importeer `tokens.css` **één keer globaal**, vóór de eigen app-CSS. In deze app
(Create React App) is dat de eerste regel van `src/index.js`:

```js
import 'nectar-brand/tokens.css';
```

Daarna gebruik je overal `var(--nectar-oranje-500)`, `var(--color-accent)`, enz.

## Een waarde wijzigen

1. Wijzig `tokens.css` hier, commit, push naar `main`.
2. In website- én app-repo de dependency verversen (zie caveat), dan deployen.

**Caveat (git-URL-dependencies):** `npm update nectar-brand` pakt niet altijd de
laatste commit bij een git-URL. Betrouwbare fallback: opnieuw installeren met de
Git-URL, eventueel met een commit-hash i.p.v. `#main`:

```bash
npm install github:Deccos-git/nectar-brand#<commit-sha>
```

## Tokens

`tokens.css` bevat kern-kleuren, categorie-kleuren, semantische kleuren,
typografie, spacing, vorm, motion en layout. Twee lagen:

- **Primitives** — `--nectar-aubergine-700`, `--nectar-oranje-500`,
  `--nectar-groen-300`, … (de merkkleuren zelf).
- **Semantisch** — `--color-bg`, `--color-accent`, `--color-text`, `--cat-1..4`
  (rollen). **Componenten binden aan deze laag**, niet aan primitives.

## Status & open (v0.3)

- Hexwaarden zijn nog **benaderingen**; de designer levert definitieve waarden.
- De categorie-kleuren (`--nectar-groen/lila/koraal/geel`, `--cat-1..4`) zijn nieuw
  en gesampeld uit de brand-deck — namen en waarden nog door de designer te
  bevestigen.
- De swatch-voorbeelden in `styleguide.html` (sectie 02) tonen nog de v0.2-waarden;
  synchroniseren zodra de definitieve hexen binnen zijn.
