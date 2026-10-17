# OG Image

> A share card for pages, rendered to PNG at build time.

Page: https://qinyangwang.github.io/ui/docs/og-image/

## Installation

```bash
npx shadcn@latest add @qinyang/og-image
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/og-image.json
```

## Usage

```tsx
import satori from "satori"
import { Resvg } from "@resvg/resvg-js"
import { OG_IMAGE_HEIGHT, OG_IMAGE_WIDTH, OgImage } from "@/components/og-image"
```

```tsx
const svg = await satori(
  <OgImage title={page.title} description={page.description} siteName="Field Notes" accent="green" fontFamily="og" />,
  {
    width: OG_IMAGE_WIDTH,
    height: OG_IMAGE_HEIGHT,
    fonts: [
      { name: "og", data: regular, weight: 400, style: "normal" },
      { name: "og", data: bold, weight: 700, style: "normal" },
    ],
  }
)
const png = new Resvg(svg).render().asPng()
```

## Examples

### Accents and Modes

Pass the site's `accent` and `mode` so the card matches the pages it links to.

```tsx
import { OG_IMAGE_HEIGHT, OG_IMAGE_WIDTH, OgImage, type OgImageProps } from "@/registry/base-nova/ui/og-image"

function Preview(props: OgImageProps) {
  return (
    <div className="overflow-hidden rounded-xl shadow-raised">
      <svg viewBox={`0 0 ${OG_IMAGE_WIDTH} ${OG_IMAGE_HEIGHT}`} role="img" aria-label={props.title} className="block h-auto w-full">
        <foreignObject width={OG_IMAGE_WIDTH} height={OG_IMAGE_HEIGHT}>
          <OgImage {...props} />
        </foreignObject>
      </svg>
    </div>
  )
}

export default function OgImageModes() {
  return (
    <div className="grid w-full max-w-3xl gap-4 sm:grid-cols-2">
      <Preview title="One accent, eight roles" siteName="Field Notes" date="Sep 2, 2026" accent="green" />
      <Preview title="One accent, eight roles" siteName="Field Notes" date="Sep 2, 2026" accent="green" mode="dark" />
      <Preview title="Small websites" siteName="Field Notes" tags={["web"]} accent="rose" />
      <Preview title="Small websites" siteName="Field Notes" tags={["web"]} accent="neutral" mode="dark" />
    </div>
  )
}
```

### CJK Titles

```tsx
import { OG_IMAGE_HEIGHT, OG_IMAGE_WIDTH, OgImage } from "@/registry/base-nova/ui/og-image"

export default function OgImageCjk() {
  return (
    <div className="w-full max-w-2xl overflow-hidden rounded-xl shadow-raised">
      <svg viewBox={`0 0 ${OG_IMAGE_WIDTH} ${OG_IMAGE_HEIGHT}`} role="img" aria-label="中文分享卡片预览" className="block h-auto w-full">
        <foreignObject width={OG_IMAGE_WIDTH} height={OG_IMAGE_HEIGHT}>
          <OgImage
            title="构建时生成分享卡片：中文标题按字符换行，最多三行"
            description="字体子集、颜色映射与深色模式。"
            siteName="田野笔记"
            author="陈米拉"
            date="2026年10月17日"
            tags={["前端", "工具"]}
            accent="violet"
            mode="dark"
          />
        </foreignObject>
      </svg>
    </div>
  )
}
```

## Rendering

The card is drawn for build-time renderers that turn JSX into SVG: inline styles, flexbox, fixed sizes on every text box and sRGB hex colours only, with no hooks, context, classes or browser APIs, so it imports from a plain script with no bundler. It is always 1200 × 630. The previews on this page draw the same component in the browser; the PNG is what gets shared.

## Fonts

The renderer reads `.ttf`, `.otf` and `.woff` files, not `.woff2`. Register one family at weights 400 and 700 and pass its name as `fontFamily`; without it the renderer's first font is used. A full CJK font is over 10 MB, so load a subset that holds only the characters on the card: a local TTF from your config, or a web font requested with a `text=` parameter (a non-browser user agent gets TTF back). Add `#`, `·` and `…` to the subset, since the tags, the byline and the clamp draw them.

## Titles

The title is clamped to three lines and sized by length, counting CJK and full-width characters double: 76px up to 28, 64px up to 48, 54px up to 80 and 46px beyond. `ogImageTitleSize(title)` returns the size. The description gets two lines under the two larger sizes and one under the smaller.

## Colours

`OG_IMAGE_TOKENS` holds the theme's background, card, foreground, muted foreground, border and primary roles for every accent in both modes. It is generated from the theme, with translucent roles flattened over the background and wide-gamut values converted to sRGB, so a theme update reaches the card when you reinstall it. `colors` overrides single roles.

## Images

`logo` (square, beside the site name) and `avatar` (round, beside the author) take a URL or a data URI of a PNG, JPEG or SVG; WebP is not supported. Both are decorative, so give the page's `og:image:alt` the title instead.

## API Reference

### OgImage

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `title` (required) | `string` | — | Clamped to three lines and sized by length. |
| `siteName` (required) | `string` | — | Shown at the top, beside `logo`. |
| `description` | `string` | — | One or two lines under the title. |
| `author` | `string` | — | Shown in the footer, before `date`. |
| `avatar` | `string` | — | Round image beside the author. |
| `logo` | `string` | — | Square image beside the site name. |
| `date` | `string` | — | Shown as given, so format it in the page's language. |
| `tags` | `string[]` | — | The first three are shown, each with a leading `#`. |
| `accent` | `"blue" \| "neutral" \| "green" \| "orange" \| "rose" \| "violet"` | `"blue"` | The theme accent preset. |
| `mode` | `"light" \| "dark"` | `"light"` | The theme mode. |
| `colors` | `Partial<OgImageColors>` | — | Overrides for single roles, on top of the accent and mode. |
| `fontFamily` | `string` | — | The family name the fonts were registered under. |
| `style` | `React.CSSProperties` | — | Merged onto the root, for a background image or a renderer quirk. |

| Data attribute | Description |
| --- | --- |
| `data-slot` | `og-image` on the root. |

### ogImageColors

`ogImageColors(accent, mode, overrides?)` returns the colours the card draws with.

### OG_IMAGE_TOKENS

The generated map, `OG_IMAGE_TOKENS[accent][mode]`, with `background`, `card`, `foreground`, `mutedForeground`, `border`, `primary`, `primaryForeground`, `primarySubtle` and `primaryBorder` as opaque hex.

### ogImageTitleSize

`ogImageTitleSize(title)` returns the title's font size in px.
