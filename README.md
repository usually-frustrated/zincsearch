# zincsearch image mirror

Upstream ZincSearch publishes its release images to a private ghcr package. This branch rebuilds them from the upstream release binaries and pushes them to `ghcr.io/usually-frustrated/zincsearch`.

```sh
docker pull ghcr.io/usually-frustrated/zincsearch:1.0.0-beta3
```

The `mirror` workflow runs every 6 hours. It syncs `main` from [zincsearch/zincsearch](https://github.com/zincsearch/zincsearch), and builds an image for any upstream release that has no image here yet. Binaries are checked against the release's `checksums.txt` before they go into the image. Run it by hand with a `tag` input to build an older release.

The images are linux/amd64 and linux/arm64. The Dockerfile is upstream's `docker/Dockerfile.release` with the license files added under `/licenses`.

This is an unofficial rebuild and is not affiliated with Zinc Labs. ZincSearch is Apache-2.0, copyright Zinc Labs Inc. and contributors; see `LICENSE` and `COPYRIGHT`.
