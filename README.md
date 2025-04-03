# Deployment Repo

Used the blueprint repo and fetched it using kpt

``` bash
BLUEPRINT_REPO=git@github.com:D-Kumar19/blueprint.git

kpt pkg get ${BLUEPRINT_REPO}/basens/@v0 backend --for-deployment

kpt fn render backend
kpt pkg tree backend

git add backend && git commit -am "initial pkg for deployment"
git push origin main
git tag backend/v0 main && git push origin backend/v0

kpt live init backend
kpt live apply backend
```
