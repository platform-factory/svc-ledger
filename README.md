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

Part of the Platform Factory reference implementation; the design seed lives
at https://github.com/thecloudgeek/platform-factory.
