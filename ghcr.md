# GitHub Container Registry (ghcr)

## How to push images to GitHub Container Registry (ghcr)

To publish an image to ghcr:

```dos
Create a Personal Access Token
Log-in to the container registry
Push an image to ghcr.io/GITHUB_USERNAME/IMAGE_NAME:VERSION
```

To access GitHub container registry you need to create Personal Access Token (PAT) on GitHub:

“Settings > Developer Settings > Personal access tokens” and create token with permissions related to “packages” (or <https://github.com/settings/tokens/new>).

After that,

```bash
export CR_PAT=YOUR_TOKEN ; echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin
```

Now, you want to tag your local images:

`docker tag SOURCE_IMAGE_NAME:VERSION ghcr.io/TARGET_OWNER/TARGET_IMAGE_NAME:VERSION`

Push re-tagged imaged to the container registry (ghcr.io):

`docker push ghcr.io/OWNER/IMAGE_NAME:VERSION`
