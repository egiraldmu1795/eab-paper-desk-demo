# A Pecar Fast Food — website

Website for **A Pecar Fast Food**, Colombian street food at 638 S Military Trail,
West Palm Beach, FL 33415.

The whole site is one file: **`index.html`**. No build step, no dependencies, no
external requests. Open it in a browser and it works; drop it on any host and it
works there too.

---

## Updating the menu

Open `index.html` and find this block near the top (about line 45):

```html
<script type="application/json" id="menu-data">
```

Everything between that tag and its closing `</script>` is the menu. Editing it
updates the category tabs, the menu sections and both languages at once.

One item looks like this:

```json
{
  "es": "Perro Paisa",
  "en": "Paisa Hot Dog",
  "d_es": "Pan, huevo de codorniz, salchicha americana…",
  "d_en": "Bun, quail egg, American sausage…",
  "price": 9.99,
  "pop": true
}
```

| Field | What it does |
|---|---|
| `es` / `en` | Item name in Spanish / English |
| `d_es` / `d_en` | Description in Spanish / English |
| `price` | A number like `9.99`. Use `null` to show "Consultar / Ask us" instead |
| `pop` | `true` puts the red **FAVORITO** badge on it |

Rules that will bite you if you break them: every value in quotes needs its
quotes, every item needs a comma after it *except the last one in a list*, and
prices are plain numbers with **no** `$` and no quotes.

## Changing opening hours

Search for `var HOURS` in the script near the bottom. Index `0` is Sunday:

```js
var HOURS = [
  { open:13, close:23 }, // Sun — 1PM to 11PM
  null,                  // Mon — closed
  { open:16, close:23 }, // Tue
  …
];
```

Times are 24-hour, in the restaurant's own timezone (America/New_York). The
site uses this for three things at once: the hours table, the "today" highlight,
and the live **Abierto ahora / Cerrado** pill in the hero — which recalculates
every minute, so it stays honest as the evening goes on.

## Changing phone / address / links

Search `index.html` for `5613775311` (WhatsApp + tel links) and
`638 S Military Trail`. Delivery links are on the three cards in the "Pide ya"
section.

---

## What's in the design

- **Bilingual.** Spanish first, English one tap away. The choice is remembered.
- **Live open/closed status**, computed in the restaurant's timezone rather than
  the visitor's, so someone browsing from another state still sees the truth.
- **Animated menu** — items stagger in as you scroll, the category bar tracks
  your position and scrolls itself to keep the active tab visible, cards lift on
  hover. All of it is disabled automatically for visitors who have
  "reduce motion" turned on.
- **Mobile order bar** that slides up once you start scrolling.
- **Schema.org restaurant markup** so Google can read the address and hours.
- No photos required — the layout is built to look finished without them.

## Adding real photos

The site deliberately ships with zero food photography. When you have real
photos of the food, they belong in a `photos/` folder next to `index.html`, and
the natural place for them is a strip above the menu section.

Please use actual photos of A Pecar's food. AI-generated or stock food images on
a restaurant site misrepresent what a customer will actually be handed, and
they're the fastest way to earn a bad first review.

## Publishing

Any static host works. For GitHub Pages: push this folder to a repo, then
**Settings → Pages → Deploy from branch**, pick the branch and the folder that
contains `index.html`.

---

## Where the content came from

Menu items, descriptions and prices were transcribed from the restaurant's
public listings on Uber Eats and Postmates. Address, phone and hours are from
the Restaurantji and AllMyLinks listings.

**A note on the name.** The site displays **A Pecar Fast Food** — the
incorporated name, and the one that makes the pun land (*a pecar* = "to sin",
which the menu already plays on with Pecador, Pecadora, La Perra, La Loba).
Every existing listing and social handle uses the closed-up spelling *Apecar*:
`@apecarfastfood` on Instagram, TikTok and Facebook, and "Apecar Fast Food" on
Uber Eats, DoorDash and Google. Those are left untouched — renaming them would
cost the 4.8★ review history. The site carries both: `A Pecar Fast Food` as the
display name, with `Apecar Fast Food`, `Apecar Fastfood` and `Apecar` listed as
`alternateName` in the Schema.org block, so a search for either spelling still
resolves here.

Two things worth confirming with the restaurant before this goes live:

1. **Prices.** Delivery-app prices are usually marked up over in-store prices,
   so these may read high at the counter. There's a note on the site saying so.
2. **Hours.** The sources disagree — Restaurantji says Tue–Fri 4–11PM,
   Sat–Sun 1–11PM, closed Monday; Uber Eats says Tue–Fri opens at 5PM. The site
   currently uses the Restaurantji version.

Three menu categories (Arepas, Maduros, Costillas de Cerdo con Papita Criolla)
are listed on Uber Eats with no items or prices attached. They're on the site
under "De la Plancha / Off the Grill" showing "Consultar / Ask us" — fill in the
real items and prices when you have them.
