# graphify-marketplace

Personal Claude plugin marketplace that wraps
[Graphify](https://github.com/Graphify-Labs/graphify) by Graphify-Labs.

## Isi

```
.claude-plugin/marketplace.json          # daftar plugin (wajib, dicari Claude)
plugins/graphify/.claude-plugin/plugin.json
plugins/graphify/skills/graphify/SKILL.md
```

Skill tidak menyalin instruksi Graphify. Skill memasang paket `graphifyy`
(versi terkunci 0.9.95), lalu membaca `skill.md` resmi dari dalam paket.

## Pasang di Claude

1. Upload repo ini ke GitHub (boleh private kalau akun GitHub sudah terhubung).
2. Claude → Settings → Plugins → Add marketplace → isi `github.com/<user>/graphify-marketplace`.
3. Install plugin `graphify`.
4. Di chat: `/graphify <folder atau URL repo>`.

Claude Code (terminal), satu langkah:

```
/plugin install graphify --marketplace <user>/graphify-marketplace
```

## Lisensi

Graphify: Apache-2.0, © Safi Shamsi and the Graphify contributors.
Repo ini hanya pembungkus; kode Graphify diambil dari PyPI saat dipakai.
