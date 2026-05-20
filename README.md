# Battery Sentinel Docker

Automated multi-arch Docker image builds of [smcneece/battery-sentinel](https://github.com/smcneece/battery-sentinel), published to GHCR.

## Images

| Registry | Image |
|----------|-------|
| GHCR | `ghcr.io/<owner>/battery-sentinel` |

Available tags:
- `<version>` — matches the upstream git tag
- `latest` — always points to the most recently built version

Supported platforms: `linux/amd64`, `linux/arm64`

## How it works

A GitHub Actions workflow runs daily at a randomized time and:

1. Polls the upstream repo for tags created within the last 7 days
2. Checks GHCR via `skopeo` to skip tags that have already been pushed
3. Builds the `addon/` directory from each unbuilt tag using `docker/build-push-action`
4. Pushes the image with both the version tag and `latest`

You can also trigger a build manually via **Actions → Build Battery Sentinel → Run workflow**, optionally specifying an exact tag to build (bypasses the 7-day filter and GHCR skip check for that tag).

## Credits

Upstream project by [smcneece](https://github.com/smcneece/battery-sentinel).
