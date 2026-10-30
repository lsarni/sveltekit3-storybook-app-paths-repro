# SvelteKit 3 + Storybook: `__SVELTEKIT_PAYLOAD__ is not defined`

Minimal reproduction: a component that imports `resolve` from `$app/paths` renders in `storybook dev`, but fails in a static `storybook build` with:

```
ReferenceError: __SVELTEKIT_PAYLOAD__ is not defined
```

## Steps

```sh
pnpm install
pnpm build-storybook
npx http-server storybook-static
```

Open the **Lib/Link → Default** story: it shows the error above.

Run `pnpm storybook` instead and the same story renders the link without errors.

## Versions

- `@sveltejs/kit` 3.1.0
- `svelte` 5.57.3
- `storybook` / `@storybook/sveltekit` 10.6.0
- `@sveltejs/vite-plugin-svelte` 7.2.0
- `vite` 8.1.5

Also reproduces with `@sveltejs/kit` 3.1.1, `storybook` / `@storybook/sveltekit` 10.6.5, `@sveltejs/vite-plugin-svelte` 7.3.1 and `vite` 8.3.5.

`pnpm-workspace.yaml` only allows esbuild's install script, which pnpm 11 otherwise refuses to run.
