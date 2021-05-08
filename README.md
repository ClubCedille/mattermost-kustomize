# mattermost-kustomize

Simple Mattermost Team Edition deployment with Kustomize.

Expects a secret named `mattermost-mattermost-team-edition-config`
containing the key `db-url` a DB connection string.

The configuration is now stored in the DB starting from release `2.0` of this repository.

Mattermost >= 5.30 expects a readable and writable configuration and
a secret configuration is read-only.

A solution with an initContainer copying the read-only configuration is possible
but we decided to move our configuration to the DB as recommended by the
Mattermost documentation.

## How to use

In your `kustomization.yaml`:

``` yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: kustomize

resources:
- github.com/ClubCedille/mattermost-kustomize?ref=2.0.0

# images:
# - name: mattermost/mattermost-team-edition
#   newTag: release-5.34
```
