# svc-ledger

The second tenant of the Platform Factory reference build, and a placeholder:
it exists so that C-05 ("onboard a second tenant with one file") has a real
service repo to point at, owned by a different team (`checkout`) than
`svc-hello` (`payments`). The workload is a stock unprivileged nginx pulled
through the platform's Docker Hub remote (ADR-0010); there is no application
code and no database claim here.

What C-05 measures is on the platform side: one `System` file in the
`systems` repo produces this service's namespace, quota, RBAC, Argo CD
project and Application, Google service account and registry — and this
`k8s/` directory is what that Application syncs, which is how "usable
namespace" is checked (a Deployment admitted under the tenant's AppProject).

## Who approves changes here

[ADR-0001](https://github.com/platform-factory/platform-factory-concept/blob/main/docs/adr/0001-repo-boundary-is-approval-boundary.md)
says the owning team approves a service repo.
[`.github/CODEOWNERS`](.github/CODEOWNERS) names `@platform-factory/platform`
instead, on purpose. The owning team is a Google Group, named once, by team,
in this service's tenant file, `systems/tenants/svc-ledger.yaml`
([ADR-0012 §3](https://github.com/platform-factory/platform-factory-concept/blob/main/docs/adr/0012-system-is-the-unit-team-is-a-field.md):
"a second file would be a second binding point"), and CODEOWNERS can name
only GitHub users and teams. A GitHub team per tenant team would be a second
place ownership is recorded, and a team move would have to edit it too.

Nothing is enforced either way yet. Every repo in this org requires zero
approvals, because GitHub does not let a pull request's author approve it and
one person authors every pull request here
([M1 log, surprise 2](https://github.com/platform-factory/platform-factory-concept/blob/main/docs/build-log/m1-spine.md)).
How a team's own approval gets enforced is M3's question (claim C-09).

Part of the Platform Factory reference implementation; the design seed lives
at https://github.com/platform-factory/platform-factory-concept.

Platform Factory was designed and written by **Ronak Patel**
([thecloudgeek LLC](https://github.com/thecloudgeek)). Licensed Apache-2.0 —
the attribution to keep is in [NOTICE](NOTICE), and
[CITATION.cff](CITATION.cff) says how to cite it.
