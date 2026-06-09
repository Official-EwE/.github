# GitVersion + Tagging (IMPORTANT)

## Problem
GitVersion may not increment versions if tags are not on trunk.
This leads to the patch Version of the package / release not being incremented.

## Root cause
Tags were created on commits not reachable from the mainline (master).

## Fix
Delete incorrect tag and recreate it on HEAD:

git tag -d vX.Y.Z
git push origin :refs/tags/vX.Y.Z
git tag vX.Y.Z
git push origin vX.Y.Z

## Prevention
Always create tags explicitly in the workflow:

git tag v${VERSION}
git push origin v${VERSION}
