# Tag release

Trigger the release action by providing a version number as an input.
This action will create a git tag, as well as a Github release.

## Permissions
```yml
permissions:
  contents: write
```

## Inputs
```yml
version:
  description: 'Version to release'
  required: true
  type: string
```

## Example workflow
```yml
name: Tag Version

on: 
  workflow_dispatch:
    inputs:
      version:
        description: 'Version to release'
        required: true
        type: string

jobs:
  release:
    name: Create github release
    permissions:
      contents: write
    uses: jpbnetley/tag-release-action/.github/workflows/action.yml@main
    with: 
      version: ${{ github.event.inputs.version }}
```