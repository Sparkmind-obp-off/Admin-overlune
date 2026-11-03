# 05 — Authentication, Perimeter & Security

## Access model
Admin is a private control plane. No public registration and no customer Clerk token may authorize Admin operations.

The previously approved preference is no in-app admin login screen. Therefore, the preferred UX is a trusted private access perimeter (for example Cloudflare Access or an equivalent verified identity-aware gateway) in front of the Admin frontend and admin API. This is a security requirement, not merely a hidden menu.

## Mandatory perimeter coverage
- Admin frontend hostname and all static/private routes.
- Every privileged API endpoint, including direct API hostname access.
- WebSocket, export, file, callback-management, and background-operation endpoints where applicable.
- Preview/staging admin surfaces must have separate policies and identities.

## Backend identity
- Validate trusted perimeter identity assertion server-side (signature, issuer, audience, expiry, allowed domain/subject, and relevant headers).
- Strip/reject client-supplied identity headers at the trusted edge; do not trust arbitrary `Cf-Access-Authenticated-User-Email` values unless the request is proven to come through the configured Access boundary and JWT is validated.
- Map stable external subject to internal admin principal; email alone is not a durable identity key.
- Apply role/permission checks after identity validation.
- Customer Clerk JWTs are accepted only on customer endpoints and never imply staff access.

## Session controls
Short-lived sessions, secure cookies, HttpOnly, Secure, appropriate SameSite, CSRF protections for cookie-authenticated mutations, origin validation, login/session revocation, step-up for sensitive actions, rate limits, and session inventory.

## Threat model
Protect against public endpoint discovery, forged identity headers, stolen sessions, CSRF, XSS, IDOR, privilege escalation, replay, webhook spoofing, secret leakage, cross-environment access, data exports, and compromised operator accounts.

## Fail-closed rule
If perimeter identity cannot be verified, deny all admin data and mutations. A public read-only synthetic demo may exist separately, but must not share production bindings or credentials. Never make real admin API routes public to avoid a login screen.

## Secret handling
Secrets are server-side Cloudflare secrets or managed secret references. UI may show configured/not-configured and masked suffix only. Never return secret values, include them in logs, or write them to Git.
