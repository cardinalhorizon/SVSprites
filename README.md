# SV Sprites

Aviation map icon sprite pack for [SimVector](https://simvector.net), built for MapLibre GL JS (and Mapbox GL JS compatible).

Each icon is a 32×32 SVG in `icons/`. The build packs them into a sprite sheet (`sprite.png` + `sprite.json`, plus `@2x` retina variants) using [spreet](https://github.com/flother/spreet).

## Icons

| Category | Icons |
| --- | --- |
| Airports | `APT_CLSD`, `APT_CTL_F`, `APT_NC_F`, `APT_NC_SF`, `APT_PVT` |
| Heliports / seaplane bases | `HPT_CTL`, `HPT_NC`, `SPT_NC`, `SPT_NC_F` |
| Navaids | `VOR`, `VOR_DME`, `VORTAC`, `DME`, `NDB`, `NDB_DME`, `LOC` |
| Waypoints / procedures | `GPS_PT`, `BP`, `DP`, `DP_MAND` |
| Traffic | `ACF_SV`, `ACF_VATSIM` |

## Usage

Install from npm, or serve the `dist/` files from any static host/CDN:

```sh
npm install @simvector/sprites
```

Point your style at the sprite **base URL without extension**. MapLibre appends `.json`, `.png`, and `@2x` automatically:

```json
{
  "version": 8,
  "sprite": "https://your-host.example/path/to/dist/sprite",
  "sources": {},
  "layers": []
}
```

Then reference icons by file name (without `.svg`):

```js
map.addLayer({
  id: 'navaids',
  type: 'symbol',
  source: 'navaids',
  layout: { 'icon-image': 'VOR', 'icon-allow-overlap': true }
});
```

## Building

Requires [spreet](https://github.com/flother/spreet) (`brew install spreet` or `cargo install spreet`).

```sh
npm run build
```

This writes `dist/sprite{,@2x}.{png,json}`. `dist/` is committed so the sprites can be consumed straight from GitHub; it is also rebuilt automatically before `npm publish`.

## Adding an icon

1. Add a 32×32 SVG to `icons/`. The file name becomes the icon name.
2. Run `npm run build` and commit the updated `dist/`.

## Contributing

Contributions are very welcome! This pack is human-made, and we'd like to keep it that way. Any SVG icon submitted must be hand-designed, and **no generative AI may be used to create the artwork**. Please include verifiable evidence of this in your pull request, for example:

- the source file from your design tool (Figma, Illustrator, Inkscape, etc.) with its version history, or
- screenshots or a screen recording of the design process, or
- earlier sketches, drafts, or iterations.

Pull requests without such evidence won't be merged. This requirement exists to keep the authorship of every icon unambiguous; see the [US Copyright Office's AI guidance](https://www.copyright.gov/ai/) for background. By contributing, you agree that your icons are released under the same [CC BY-SA 4.0](LICENSE) license as the rest of the pack.

## License and attribution

Licensed under [CC BY-SA 4.0](LICENSE). Adaptations must be shared under the same license.

**Authorship.** All icon artwork in `icons/` was designed by humans. It is original, copyrighted work, not public domain and not AI-generated. AI tools may have been used to help manage this repository (tooling, commits, and pushes). Where such tools attribute themselves, for example in commit metadata, that attribution does not reflect who created the artwork, and it does not affect the copyright or license of the icons.

**Attribution on maps.** When these icons are displayed in a map, credit them in the map's attribution/copyright notice, for example:

```
Icons © SimVector (CC BY-SA 4.0)
```

**Exception for SimVector tiles.** If your map uses SimVector map tiles, the SimVector tile attribution already covers these icons, so you may omit the separate icon credit to keep the notice uncluttered. This is an additional permission granted by the copyright holder; all other CC BY-SA 4.0 terms still apply, including when you redistribute the icons themselves.
