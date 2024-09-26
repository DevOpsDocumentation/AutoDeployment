# AutoDeployment

## build_and_push.yaml 
- Previously used to build and push docker-images to ghcr
- Image name: repository name 
- triggered on: push from dev and main

- New changes adds build-push-and-deploy
- It converts REPONAME to repo_name(snake_case) and it is further used as service name 
- If service to be deployed is not same as repo name in snake_case we set GITHUB VARIABLE having name of the service to be deployed
- We are using PAT to trigger deploy workflow in devops repo, ----> saving PAT in the repo whose service is to be deployed
- We are using this dispatch github API for this, `https://api.github.com/repos/${{ github.repository_owner }}/${{ vars.DEVOPS_REPO_NAME || 'devops' }}/dispatches \` 
