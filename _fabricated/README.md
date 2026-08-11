# Quarantined — API Evangelist authored, NOT published by Casetext

Everything in this directory was **written by API Evangelist tooling**, not harvested from
Casetext. It is kept for audit history and deliberately held outside the artifact
directories so it can never be indexed, scored, or read as a provider-published contract.

## `graphql/` — quarantined 2026-08-10

`casetext-schema.graphql` (23KB, ~600 lines of SDL) and `casetext-graphql.md` were a
**conceptual model**, not a harvested schema. The files say so themselves:

> "This conceptual GraphQL schema models the Casetext AI legal research platform"
> "There is no public developer API; this schema is a conceptual model based on publicly
> documented platform capabilities."

Despite that, `apis.yml` carried `type: GraphQL → graphql/casetext-graphql.md`, which asserts
to every downstream consumer (apis.io, the Kin Score contract facet, the GraphQL aggregation
site) that **Casetext publishes a GraphQL API**. It does not, and never did. The pointer was
removed from `apis.yml` in the same pass that moved these files here.

The schema also invents an access-control surface Casetext never shipped — `APIKey`, `Token`,
`RateLimitInfo` types and a `createAPIKey` mutation — which is precisely the shape that gets
mistaken for evidence of a developer program.

### Verification that no GraphQL surface exists

| URL | Status | Observed 2026-08-10 |
|---|---|---|
| `https://casetext.com/graphql` | **410** | Gone |
| `https://casetext.com/openapi.json` | **410** | Gone |
| `https://casetext.com/swagger.json` | **410** | Gone |
| `api.casetext.com`, `developer.casetext.com`, `docs.casetext.com` | — | do not resolve (NXDOMAIN) |

See `../apis.yml` → `x-coverage` for the full retirement evidence.

**Do not restore these files to `graphql/`.** If Thomson Reuters ever publishes a real
CoCounsel contract it belongs in the `thomson-reuters` repo, harvested verbatim.
