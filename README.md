# Hackify

I HACKED hackify.io, SO I AM LEAKING THE SOURCE CODE LOL, also, this privacy matters guy is trash, he does NOT know how to program or how to hack, actually learn shit u dumb piece of shit "privacy matters"

(make sure python is installed in your computer, if it isnt, install it here: https://www.python.org/downloads/ )

## here is how to operate :)

1. Open a terminal in the directory you downloaded the files:

```bash
cd <DIRECTORY>
```
you can also just right click it and click "open in terminal"

2. Start a local HTTP server:

```bash
python3 -m http.server 8765
```

3. Open in browser:

```
http://localhost:8765/
```

> **Important:** Must be served via HTTP. Opening `index.html` directly as `file://` will NOT work because the JS uses ES modules which require HTTP due to CORS restrictions.

## Auth System

The app uses three roles:

| Role | Level | Description |
|------|-------|-------------|
| `basic` | 1 | Free user |
| `pro` | 2 | Paid user |
| `admin` | 3 | Administrator (highest) |

There is no "owner" role.

## Standalone Version (hackify.html)

The `hackify.html` file is a fully self-contained single HTML file (~3MB) that includes:

- All CSS inlined in a `<style>` tag
- All JS base64-encoded and loaded via Blob URL

This approach was necessary because the JS bundle contains a `</script>` string inside an XSS example payload, which would prematurely close an inline `<script>` tag.

> **Note:** `hackify.html` must also be served via HTTP at the root path (`/`) to work with React Router. It cannot be opened as a local file.

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Black screen | Make sure you're accessing via `http://localhost:8765/`, not `file://` |
| 404 page | React Router requires the URL path to match a route. Use `/` not `/hackify.html` |
| `row-level security policy` errors | Expected. Admin operations require real admin role in Supabase DB |
| Server not starting | Make sure Python 3 is installed and port 8765 is free |
