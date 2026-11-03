# Inter-service communication

Canonical flow:

Console -> Control Server -> Device Gateway -> enrolled Android agent
Control Server -> Mobile Sync -> authorized contacts/media providers

The Contracts SDK is the contract authority. All services consume openapi/mobile-control.yaml.

## Rules
- JWT/OIDC at public and service boundaries; no credentials in payloads.
- Mutations carry idempotency and actor identity.
- Commands are durable and asynchronous.
- Device readback/results are authoritative for completion.
- Destructive actions require RBAC and audit events.
- No endpoint bypasses Android security, MFA, banking verification, or third-party app sandboxes.