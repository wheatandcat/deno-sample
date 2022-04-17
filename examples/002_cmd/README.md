# deno

## 実行

### curl

```bash
$ deno run --allow-net ./curl.ts https://example.com
```

### cat

```bash
$ deno run --allow-read ./cat.ts /etc/hosts
```

### remote

```bash
$ deno run ./remote.ts
```

## コマンドライン

### Help

```bash
$ deno -h
```

```bash
$ deno bundle -h
```

### Script source


```bash
$ deno run main.ts
$ deno run https://mydomain.com/main.ts
$ cat main.ts | deno run -
```

### Allow

```bash
$ deno run --allow-net net_client.ts
$ deno run --allow-read net_client.ts
$ deno run --allow-net=example.com net_client.ts
```

### Watch mode

```bash
$ deno run --watch main.ts
$ deno test --watch
$ deno fmt --watch
```

### Integrity flags

Affect commands which can download resources to the cache: deno cache, deno run, deno test, deno bundle, deno doc, and deno compile.

```bash
--lock <FILE>    Check the specified lock file
--lock-write     Write lock file. Use with --lock.
```


### Cache and compilation flags

```bash
--config <FILE>               Load configuration file
--import-map <FILE>           Load import map file
--no-remote                   Do not resolve remote modules
--reload=<CACHE_BLOCKLIST>    Reload source code cache (recompile TypeScript)
--unstable                    Enable unstable APIs
```

### Debugging use break point

```bash
$ deno run --inspect-brk --allow-read --allow-net https://deno.land/std@0.135.0/http/file_server.ts
```

```bash
$ open chrome://inspect
```