# Dispatches
General entrypoint for github repository dispatches for micro-commnity.

This repo defines workflows for processing [repository dispatch events](https://docs.github.com/en/free-pro-team@latest/rest/reference/repos#create-a-repository-dispatch-event). We rely on github.com/micro-community/micro to push events to this repo when something interesting happens (e.g. a new push to master etc) and we then take action. We currently do the following:
- build and push the crazybber/platform image to Github Container Registry
- build and push the craybber/cells images to Github Container Registry

## Manually triggering builds
You can manually trigger builds if required. 
```
$ curl -X POST -H "Authorization: token $GH_REPO_DISPATCH_PAT" -H "Accept: application/vnd.github.v3+json"   https://api.github.com/repos/micro-community/dispatches/dispatches -d '{"event_type":"micro_release"}' 
```
