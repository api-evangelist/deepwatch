# Deepwatch

Deepwatch is a US managed security services provider delivering AI-native managed detection and response (MDR) governed by human security experts. Its Guardian platform and Security Center console correlate telemetry from a customer's existing SIEM, EDR, cloud, identity, network and vulnerability tooling rather than requiring a rip-and-replace.

- Website: https://www.deepwatch.com/
- Security Center console: https://devportal.deepwatch.com/
- Status: https://status.deepwatch.com/
- Trust center: https://security.deepwatch.com/
- Legal / service descriptions / SLA: https://legal.deepwatch.com/

## API surface

Deepwatch publishes **no public API documentation, OpenAPI or SDK**. The customer-facing
contract is an authenticated GraphQL API (AWS AppSync) at
`https://devportalapi.deepwatch.com/graphql/`, discovered in the Security Center console
bundle and advertised with a realtime WebSocket channel in the console's CSP. Anonymous
introspection is refused by a WAF rule (HTTP 403 `WAFForbiddenException`); access is gated
behind Okta-brokered single sign-on.

## Artifacts

| Dir | File | Method |
|---|---|---|
| `llms/` | `deepwatch-llms.txt` | searched (verbatim from `www.deepwatch.com/llms.txt`) |
| `well-known/` | `deepwatch-well-known.yml`, `deepwatch-openid-configuration.json` | probed |
| `authentication/` | `deepwatch-authentication.yml` | searched |
| `scopes/` | `deepwatch-scopes.yml` | searched |
| `conventions/` | `deepwatch-conventions.yml` | derived |
| `conformance/` | `deepwatch-conformance.yml` | searched |
| `lifecycle/` | `deepwatch-lifecycle.yml` | searched (SLA, status page, service descriptions) |
| `security/` | `deepwatch-domain-security.yml` | probed |
| `security/` | `deepwatch-vulnerability-disclosure.yml` | searched |
| `security/` | `deepwatch-trust-center.yml` | searched |

Not present, and deliberately not authored: no OpenAPI, AsyncAPI, webhooks, MCP server,
A2A agent card, SDKs/packages, CLI, sandbox, changelog or public error catalog were found.
