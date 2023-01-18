# GitHub Container Registry (ghcr)

## How to push images to GitHub Container Registry (ghcr)

To publish an image to ghcr:

```dos
Create a Personal Access Token
Log-in to the container registry
Push an image to ghcr.io/GITHUB_USERNAME/IMAGE_NAME:VERSION
```

### Create a Personal Access Token (PAT) for GitHub

“Settings > Developer Settings > Personal access tokens” and create token with permissions related to “packages” (or <https://github.com/settings/tokens/new>).

### Docker login to ghcr

Unix / Mac:

```bash
export CR_PAT=YOUR_TOKEN
echo $CR_PAT | docker login ghcr.io -u briansu2004 --password-stdin
```

Windows:

```bash
docker login ghcr.io -u briansu2004
```

### Tag local images

`docker tag SOURCE_IMAGE_NAME:VERSION ghcr.io/TARGET_OWNER/TARGET_IMAGE_NAME:VERSION`

### Push re-tagged images to ghcr

`docker push ghcr.io/OWNER/IMAGE_NAME:VERSION`

e.g.

```dos
C:\Code\MyGitHub>docker login ghcr.io -u briansu2004                 
Password: 
Login Succeeded
C:\Code\MyGitHub>docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE  
color-web    init      2454b6595e3c   13 minutes ago   60.4MB

C:\Code\MyGitHub>docker tag color-web:init ghcr.io/briansu2004/colorweb:latest

C:\Code\MyGitHub>docker images
REPOSITORY                                        TAG        IMAGE ID       CREATED          SIZE  
color-web                                         init       2454b6595e3c   15 minutes ago   60.4MB
ghcr.io/briansu2004/colorweb                      latest     2454b6595e3c   15 minutes ago   60.4MB

```
