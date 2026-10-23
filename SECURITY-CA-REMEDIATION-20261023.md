# CA security remediation — 23 October2026

Cargo.lock updated rustls-webpki0.103.9->0.103.16, webpki-roots and webpki-root-certs1.0.6->1.0.10. Cargo also reconciled the existing notify windows-sys dependency edge0.52->0.59; no other package versions changed. cargo check --locked -p openfang-kernel passes; cargo test --locked -p openfang-runtime web_fetch --lib:5passed. No agent started or binary installed. Deployed process version unknown; no deployment target established. Untracked desktop schema and smoke project preserved.

Source: https://render.com/docs/advisory-emudhra
Synectics remains archived. No credential changes. No Production mutations.

## Follow-up validation

Docker build now uses cargo build --locked to preserve corrected trust dependencies. Kernel cargo check --locked --offline passes after change; prior5HTTP/SSRF tests passed. Process-path scan found no active local OpenFang process and no matching launchagent. No hosted target identified in reviewed docs/config, which is not proof no external deployment exists. No binary installed or agent started.

## Evening validation — 23 October 2026

Read-only scope: no service/container/agent start, deployment, credential change,
Git staging/commit/push or Synectics/Sorcer reactivation.

- `cargo check --locked --offline -p openfang-kernel`: passed.
- `cargo test --locked --offline -p openfang-runtime web_fetch --lib`: 5 passed;
  tests inspect SSRF rules without starting a server.
- Temporary HTTPS probe outside the repository, using the application's Reqwest
  0.12.28 feature selection and matching rustls0.23.36, rustls-webpki0.103.16,
  webpki-roots1.0.10: public control render.com returned200; both test endpoints
  linked by Render rejected with InvalidCertificate/CertDistrusted. No proxy,
  credential or agent used. This validates the TLS stack, not a deployed binary.
- `git diff --check`: passed.

No Docker image built or daemon started. Existing external deployment/binary
versions remain unestablished. Tokio native-root WebSocket paths and system CA
trust are distinct from the tested Reqwest bundled-root path; no complete live
integration claim. Existing Cargo/Docker fixes remain local, uncommitted.
Source: https://render.com/docs/advisory-emudhra (reviewed23October2026).
