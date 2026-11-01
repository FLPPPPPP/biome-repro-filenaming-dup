# Biome: `useFilenamingConvention` reports a `.vue` file once per embedded snippet

Minimal reproduction for a Biome bug report. Biome 2.6.4.

## Steps

```sh
npm install
npx biome lint src
```

## Actual

The same `useFilenamingConvention` diagnostic for `src/FooBar.vue` is printed 4 times ("Found 4 errors."): once for the `<script>` block and once for each of the three `{{ }}` interpolations. With `html.experimentalFullSupportEnabled` set to `false`, it is printed once.

## Expected

One diagnostic per file, whatever the number of template expressions.
