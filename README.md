# Nuvio webOS Homebrew Repository

A small self-hosted repository for the LG webOS build of Nuvio Native Legacy.

Source project:
https://github.com/iqui27/nuvio-native-legacy

## Automatic updates

The GitHub Actions workflow checks the upstream Nuvio GitHub Releases API and:

1. Finds the latest stable release.
2. Selects the standard LG webOS `.ipk` (`*_arm.ipk`, not the `highcache` build).
3. Downloads the package temporarily.
4. Calculates its SHA-256 and size.
5. Generates `repo.json` in the format used by webOS Homebrew Channel.
6. Commits `repo.json` if the upstream version changed.

It runs once per day and can also be started manually from **Actions → Update Nuvio repository**.

## Adding it to Homebrew Channel

After the first successful workflow run, add this URL as an external repository in Homebrew Channel:

`https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/YOUR_REPOSITORY/main/repo.json`

Replace `YOUR_GITHUB_USERNAME/YOUR_REPOSITORY` with your actual GitHub repository.

Homebrew Channel supports external repositories. See:
https://github.com/webosbrew/webos-homebrew-channel

## Important

This repository does not redistribute or modify Nuvio's source code. It points Homebrew Channel at the upstream GitHub release asset.

The workflow deliberately chooses the normal LG `.ipk` and does not choose the optional `highcache` build.

The upstream project currently states that its LG `.ipk` builds target webOS 3 and newer.
