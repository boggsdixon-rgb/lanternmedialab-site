# Security Policy

This site is a static HTML/CSS site with no server-side code, database, or
login system, served via GitHub Pages. There is no application backend to
exploit (no SQL injection, no server RCE, no session/auth surface). The main
residual risks are at the infrastructure layer: the GitHub account/repo, the
domain registrar account, and DNS.

## Reporting a vulnerability

Email lanternlabs@lanternmedialab.com or see `/.well-known/security.txt`.

## Hardening in place

- Content-Security-Policy meta tag: blocks all script execution
  (`script-src 'none'`) and restricts other resource loading to same-origin.
- No third-party scripts, trackers, or CDN dependencies are loaded.
- Forms submit via `mailto:` — there is no form backend to attack.
- GitHub secret scanning + push protection enabled on the repo.
- HTTPS will be enforced on the custom domain once DNS is verified and
  GitHub issues the TLS certificate (cannot be enabled before DNS points
  here — see main repo notes).

## Owner-side hardening recommended (outside this repo)

- Enable 2FA on the GitHub account and the domain registrar (Squarespace)
  account — these are the actual keys to this site, not anything in the code.
- Keep the domain's registrar lock / transfer-lock enabled.
- Avoid adding third-party JavaScript (analytics widgets, chat embeds, etc.)
  without reviewing them — each one is a new supply-chain risk and would
  require loosening the CSP above.
