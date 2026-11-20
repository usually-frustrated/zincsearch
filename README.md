# zincsearch image mirror

This fork publishes public container images for current ZincSearch releases at `ghcr.io/usually-frustrated/zincsearch`.

## Why this fork exists

Upstream builds its 1.x release images into `ghcr.io/zincsearch/zincsearch`, and that package is private, so nobody outside the upstream org can pull it. The public images elsewhere stop at 0.4.x: `public.ecr.aws/zinclabs/zincsearch` and the Docker Hub mirrors all end there. We wanted a pullable image of the current release to use as a small Elasticsearch stand-in for test environments, so this fork rebuilds it from upstream's own release binaries.

The fork changes no ZincSearch code. `main` tracks upstream as-is, and everything added here lives on the `mirror` branch.

## Usage

```sh
docker pull ghcr.io/usually-frustrated/zincsearch:1.0.0-beta3
```

The `mirror` workflow runs every 6 hours. It syncs `main` from [zincsearch/zincsearch](https://github.com/zincsearch/zincsearch), and builds an image for any upstream release that has no image here yet. Binaries are checked against the release's `checksums.txt` before they go into the image. Run it by hand with a `tag` input to build an older release.

The images are linux/amd64 and linux/arm64. The Dockerfile is upstream's `docker/Dockerfile.release` with the license files added under `/licenses`.

This is an unofficial rebuild and is not affiliated with Zinc Labs. ZincSearch is Apache-2.0, copyright Zinc Labs Inc. and contributors; see `LICENSE` and `COPYRIGHT`.
