---
title: "Testing GitHub Actions Workflow"
date: 2025-06-24T07:22:00-03:00
draft: false
tags: ["github-actions", "docker", "hugo", "devops"]
categories: ["Development"]
description: "Testing our automated Docker build and deployment pipeline with GitHub Actions"
---

# Testing GitHub Actions Workflow

Today I'm testing our automated GitHub Actions workflow that builds and pushes Docker images whenever we push new content to the blog.

## What happens when I publish this post?

When I commit and push this post to the `main` branch, the following should happen automatically:

1. **GitHub Actions triggers** - The workflow defined in `.github/workflows/docker.yml` will start
2. **Docker image builds** - Hugo will generate the static site and package it into a Docker container
3. **Image gets pushed** - The new Docker image will be pushed to GitHub Container Registry (ghcr.io)
4. **Multiple tags created**:
    - `latest` (since this is the main branch)
    - `main` (branch name)
    - `sha-<commit-hash>` (specific commit identifier)

## Why Docker?

Using Docker for our Hugo blog gives us several benefits:

-   **Consistent deployments** - Same environment everywhere
-   **Easy scaling** - Can deploy anywhere that supports containers
-   **Version control** - Each commit gets its own tagged image
-   **Rollback capability** - Easy to revert to previous versions

## GitHub Actions Workflow

Our workflow is configured to:

-   Trigger on pushes to `main` branch
-   Trigger on version tags (like `v1.0.0`)
-   Build using the Hugo Docker image
-   Push to GitHub Container Registry
-   Create semantic version tags when we push Git tags

Let's see if everything works as expected! 🚀

## Next Steps

After this post is published, I can:

-   Check the Actions tab to see the workflow run
-   Verify the Docker image was created in the Container Registry
-   Test deploying the new image

---

_This post was created to test our CI/CD pipeline. Pretty cool that this entire process is automated!_
