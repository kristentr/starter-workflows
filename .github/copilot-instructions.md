# GitHub Copilot Instructions for Starter Workflows

## Project Overview
This repository contains GitHub Actions starter workflow templates, organized by category (ci/, code-scanning/, deployments/, automation/, pages/). Each workflow consists of a YAML file and metadata in `properties/*.properties.json`.

## Workflow Structure
- **YAML File**: Defines the GitHub Actions workflow (e.g., `ci/node.js.yml`)
- **Properties JSON**: Contains metadata like name, description, categories, icon (e.g., `ci/properties/node.js.properties.json`)
- **Icons**: SVG files in `icons/` or octicon references

## Key Conventions
- **Action Pinning**: Always pin third-party actions to specific SHA commits (e.g., `uses: actions/checkout@v4` → `uses: actions/checkout@<SHA>`)
- **Variables**: Use repository variables like `$default-branch`, `$protected-branches`, `$cron-daily`
- **Categories**: Choose from predefined list (continuous-integration, deployment, etc.) and match detected languages/tech stacks
- **Simplicity**: Keep workflows minimal; avoid paid services or unnecessary third-party data sharing
- **Preview Mode**: Add `"labels": ["preview"]` to properties.json to hide from public; remove to publish

## Validation & Testing
- **Local Validation**: Run `npm ci && npx ts-node-script ./index.ts` in `script/validate-data/` to validate YAML syntax and JSON schema
- **CI Checks**: Automatic validation on push/PR via `.github/workflows/validate-data.yaml`
- **Linting**: Pre-commit hooks check trailing whitespace in workflow files
- **Preview Testing**: Use `?preview=true` query param on Actions page to view hidden templates

## Adding New Workflows
1. Create `.yml` in appropriate category folder
2. Add corresponding `.properties.json` in `properties/` subfolder
3. Add SVG icon to `icons/` if needed, or use octicon format
4. Ensure unique `name` across all workflows
5. Test with preview label, then remove for public release

## Current Focus
Only accepting new code-scanning workflows at this time. See `CONTRIBUTING.md` for guidelines.

## Example Properties
```json
{
  "name": "Node.js",
  "description": "Build and test a Node.js project with npm.",
  "iconName": "nodejs",
  "categories": ["Continuous integration", "JavaScript", "npm"],
  "creator": "GitHub"
}
```

Reference: `README.md` for full category list and variable details.