# Photos

Drop food photos in this folder, then list them in the `photos` array inside
the `menu-data` block at the top of `../index.html`:

```json
"photos": [
  { "file": "perro-paisa.jpg", "es": "Perro Paisa", "en": "Paisa Hot Dog" },
  { "file": "ranchera.jpg",    "es": "Hamburguesa Ranchera", "en": "Ranchera Burger" }
]
```

To also put a photo on a menu card, add `"img"` to that item:

```json
{ "es": "Paisa", "en": "Paisa", "price": 9.99, "img": "perro-paisa.jpg" }
```

## Behaviour

- While the `photos` array is empty, the whole gallery section stays hidden —
  the site looks finished with zero photos.
- A filename that doesn't resolve is dropped silently rather than showing a
  broken-image box, so a typo degrades quietly instead of breaking the page.

## Shooting notes

- **Portrait, roughly 4:5.** Tiles are cropped to that ratio; a landscape shot
  loses its top and bottom.
- **Shoot in daylight or under the truck's own lights** — phone flash flattens
  food and turns the cheese grey.
- Resize to about **1200px on the long edge** and save as JPEG around quality
  80. Straight-off-the-phone files are 4-6MB each and will make the page crawl
  on someone's mobile data.
- Around 4 to 8 photos is the sweet spot — enough to fill the grid, few enough
  that every one is a good one.
