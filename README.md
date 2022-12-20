# Quarkus Update Recipes

This repository contains the recipes used by the Quarkus tooling to update Quarkus projects to newer versions.

The recipes are contained in the `recipes/**` directory and follow a pattern. Recipes are named `name-[major.minor].yaml` (i.e. `quarkus-3.0.yaml`).

Given:
- `currentVersion` the current Quarkus core version of the project
- `targetVersion` the target Quarkus core version to update to 
- `recipeVersion` the version of the recipe file

Then, the recipe is applied if (only comparing major.minor):
`currentVersion < recipeVersion AND targetVersion >= recipeVersion`.

The Quarkus tooling will always use the latest GitHub release of the recipe directory.

Example:

Content of the `recipes/**` directory:
- quarkus-2.7.yaml
- quarkus-2.9.yaml
- quarkus-3.0.yaml
- quarkus-3.1.yaml
- quarkus-3.5.yaml

Recipes applied for a project in version 2.0.0.Final updating to 3.0.0.Alpha1 (`currentVersion=2.0`, `targetVersion=3.0`):
- quarkus-2.7.yaml
- quarkus-2.9.yaml
- quarkus-3.0.yaml

Recipes applied for a project in version 2.7.0.Final updating to 3.1.0.Final (`currentVersion=2.0`, `targetVersion=3.0`):
- quarkus-2.9.yaml
- quarkus-3.0.yaml
- quarkus-3.1.yaml