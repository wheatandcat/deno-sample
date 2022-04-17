# deno

## deps.ts run

```bash
$ deno run test.ts
```
## use vendor

```bash
$ deno vendor ./test.ts
$ deno run -A --import-map vendor/import_map.json ./test.ts
```

## cache reload

```bash
$ deno cache --reload ./test.ts
```

## Private modules and repositories

```bash
$ DENO_AUTH_TOKENS=a1b2c3d4e5f6@deno.land
```