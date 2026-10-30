# `vite preview` logs every request, `vite dev` doesn't

A minimal Worker with `@cloudflare/vite-plugin` 1.66.0 and `vite` 8.3.5.

```sh
npm i

# 1. Dev: no request lines.
npx vite --port 5197
curl http://localhost:5197/hello   # in another shell, then Ctrl+C the server

# 2. Preview: a line for every request.
npx vite build
npx vite preview --port 5197
curl http://localhost:5197/hello   # in another shell
```

**Dev** prints nothing for the request.

**Preview** prints one line per request:

```
GET /hello 200 OK (3ms)
```

The dev Miniflare options set `logRequests: false`; the preview options leave Miniflare's default,
`true`.
