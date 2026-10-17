# Introduction

Page: https://qinyangwang.github.io/ui/docs/

186 React components, blocks and templates you install as source with the shadcn CLI.

qinyang/ui is a shadcn registry, not an npm package. Add the `@qinyang` namespace to your project once, then the CLI copies each component and its dependencies into your codebase. From then on the code is yours.

Use it for app interfaces. Start from a template when you want the pieces already wired together.

## Principles

- **Open code**: Every item installs into your project as source through the shadcn CLI. To change a component, edit its file.
- **Native desktop style**: Sizes and surfaces are tuned for dense app screens rather than marketing pages.
- **Accessible primitives**: Interactive parts sit on headless primitives, so focus, keyboard and ARIA behaviour come built in.
- **Motion with restraint**: Animations settle without bounce, and each one becomes a cross-fade when the user prefers reduced motion.
- **Tokens only**: Components read theme tokens, never raw colours, so a theme or accent change restyles everything at once. Lint rules enforce it.

## What's inside

- [Foundations](https://qinyangwang.github.io/ui/#foundations)
- [Forms](https://qinyangwang.github.io/ui/#forms)
- [Overlays](https://qinyangwang.github.io/ui/#overlays)
- [Display](https://qinyangwang.github.io/ui/#display)
- [Navigation](https://qinyangwang.github.io/ui/#navigation)
- [Text](https://qinyangwang.github.io/ui/#text)
- [Motion](https://qinyangwang.github.io/ui/#motion)
- [Data](https://qinyangwang.github.io/ui/#data)
- [Agents](https://qinyangwang.github.io/ui/#agents)
- [Charts](https://qinyangwang.github.io/ui/#charts)
- [Blocks](https://qinyangwang.github.io/ui/#blocks)
- [Templates](https://qinyangwang.github.io/ui/#templates)

## Stack

- Headless primitives for interactive parts (the `base-nova` style).
- [Tailwind CSS 4](https://tailwindcss.com) with CSS-variable tokens declared in `@theme inline`.
- `motion/react` for springs and layout animation.
- The [shadcn CLI](https://ui.shadcn.com/docs/cli) for distribution, and an icon set shipped as `@qinyang/icons`.

## Quick start

Add the namespace (see [Installation](https://qinyangwang.github.io/ui/docs/installation/)), then install the theme and a first component.

```bash
pnpm dlx shadcn@latest add @qinyang/theme @qinyang/button
```

- [Installation](https://qinyangwang.github.io/ui/docs/installation/)
- [Browse components](https://qinyangwang.github.io/ui/)
