# identity-mismatch

Research tooling for **authorized** web/container security testing.

`identity_oracle.html` fingerprints the context it is loaded into and reports where the
layers disagree about identity:

- **claimed identity** — origin, scheme, secure context, frame ancestry, opener
- **recorded permission state** — `permissions.query`, exposed device labels
- **container surface** — which native bridge (if any) is reachable
- **policy** — `Permissions-Policy` / `featurePolicy` for camera, microphone, display-capture
- **non-getUserMedia capture routes** available in this context

It then flags divergences between those layers — e.g. a cross-origin frame that can still
reach the camera, or device labels exposed while the permission store reports "prompt".

**Passive by default.** Nothing triggers a permission prompt until an explicit ACTIVE
button is pressed.

Intended for testing systems you own or are authorized to test under a bug bounty /
responsible disclosure programme.
