# Uncommon Dockerfile Bug: Image Bloat and Inconsistent Behavior

This repository demonstrates a common but often overlooked issue in Dockerfiles: using a generic base image and neglecting cleanup steps.  This can lead to unnecessarily large images and unpredictable behavior due to inconsistencies between different versions of the base image.

## Bug

The `Dockerfile` uses `ubuntu:latest`, which is very generic. This results in a larger image size than necessary, and the exact contents of the image will change depending on when the image is built.  There's also no `apt-get clean` or `apt-get autoremove` to remove downloaded packages and dependencies which further increases the size.

## Solution

The `Dockerfile.fixed` addresses these issues by using a smaller, more specific base image and adding clean up steps.  This results in a smaller, more consistent, and predictable image.
