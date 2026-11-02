# Linkwarden (LazyCat LPK)

Collaborative bookmark manager with page archival.

- Upstream: https://github.com/linkwarden/linkwarden
- Image: ghcr.io/linkwarden/linkwarden:v2.16.3 (mirror mode, digest-matched)
- License: AGPL-3.0 (full text in `content/licenses/LICENSE.md`)
- Containers: Linkwarden + PostgreSQL 16 + Meilisearch v1.13.3

## Notes

- Version resolved by paging GHCR's tag list in full; the Docker Hub repo is empty, so this
  only works because the Action supports GHCR sources.
- No admin-seeding env var upstream: the first account is self-registered
  (`NEXT_PUBLIC_DISABLE_REGISTRATION=false` keeps registration open for that first signup).
- `NEXTAUTH_URL` must include the `/api/v1/auth` suffix and use the app's https domain,
  otherwise auth callbacks break behind the proxy.
- DB password, `NEXTAUTH_SECRET` and the Meilisearch key all come from platform stable secrets.
- Page snapshots require outbound network access to the target site.
- Data on `/lzcapp/var/{pgdata,meili,data}`.
- No mail service configured.
- Not yet verified on a real device.
