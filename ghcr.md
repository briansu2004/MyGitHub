# GitHub Container Registry (ghcr)

## How to push images to GitHub Container Registry (ghcr)

To publish an image to ghcr

```dos
Create a Personal Access Token
Login to the container registry
Tag local images
Push re-tagged images to ghcr
```

### Create a Personal Access Token (PAT) for GitHub

“Settings > Developer Settings > Personal access tokens” and create token with permissions related to “packages” (or <https://github.com/settings/tokens/new>).

![1674058028727](image/ghcr/1674058028727.png)

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

C:\Code\MyGitHub>docker push ghcr.io/briansu2004/colorweb:latest
The push refers to repository [ghcr.io/briansu2004/colorweb]
3b7bbc716e20: Pushed
5f70bf18a086: Mounted from briansu2004/udemy-devops-9projects-free
d42ba8aa32b4: Pushed
a57d572a019a: Pushed
8b3fb03be45e: Pushed
a2fbf44956f8: Pushed
db02c1e68eb7: Pushed
4efbcf210682: Mounted from briansu2004/udemy-devops-9projects-free
8e012198eea1: Mounted from briansu2004/udemy-devops-9projects-free
latest: digest: sha256:7c7a6433eef703112976f490a36252968f39be4ae7a81447cf0b4c16359eaaf7 size: 2202
```
