# Welcome

Roo Code Marketplace is an un-released work in progress.....

Imagine effortlessly gliding through your projects with the agility of a kangaroo on Roo mode! 🦘 Picture your data flowing seamlessly and powerfully through our mighty MCP servers, like a vibrant river of information! 🌊 And get ready to craft spells of efficiency and innovation with the perfect prompts – your secret incantations for mastery!

Sharing is caring, and when you share your knowledge of Roo modes, MCP servers, and brilliant prompts, you're not just helping your team – you're spreading happiness throughout the Roo community! 😊 Watch as collaboration soars, productivity skyrockets, and smiles bloom across faces. It's a roovolution of joy and empowerment!

So, dive in, explore the wonders of Roo modes, harness the strength of MCP servers, and play with the power of prompts. Unleash your superpowers and let the happiness flow! 🚀 You've got this! 💪

This guide explains how to create and share Modes, MCPs, and Prompts to Roo Code users conviniently available right inside Roo.  

[Learn more about using Roo Code Marketplace](https://github.com/Smartsheet-JB-Brown/Roo-Code/blob/jbbrown/marketplace/cline_docs/marketplace/README.md)

## Item Structure, Metadata, and Features

### Overview

* Every component on the registry is an `item`.
* An `item` can be of type: `mcp`, `mode`, `prompt`, `package`
* Each item apart from `package` is a singular object, i.e: one mode, one mcp server.
* A `package` contains multiple other `item`s
  * All internal sub-items of a `package` is contained in the binary on the `package` item metadata itself.
* Each `item` requires specific metadata files and follows a consistent directory structure.

### Directory Structure

The `registry` structure could be the root or placed in a `registry` directory of any `git` repository, a sample structure for a registry is:

```
registry/
├── metadata.en.yml               # Required metadata for the registry
│
├── modes/                        # `mode` items
│   └── a-mode-name/
│       └── metadata.en.yml
├── mcps/                         # `mcp` items
├── prompts/                      # `prompt` items
│
└── packages/                     # `package` items
    └── a-package-name/
        ├── metadata.en.yml       # Required metadata
        ├── metadata.fr.yml       # Optional localized metadata (French)
        ├── modes/                # `a-package-name`'s internal `mode` items
        │   └── my-mode/
        │       └── metadata.en.yml
        ├── mcps/                 # `a-package-name`'s internal `mcp` items
        │   └── my-server/
        │       └── metadata.en.yml
        └── prompts/              # `a-package-name`'s internal `prompt` items
            └── my-prompt/
                └── metadata.en.yml
```

### Metadata File Format

Metadata files use YAML format and must include specific fields:

#### `registry`:
```yaml
name: "My Registry"
description: "A concise description for your registry"
version: "0.0.0"
author: "your name" # optional
authorUrl: "http://your.profile.url/" # optional
```

#### `item`:
```yaml
name: "My Package"
description: "A concise description for your package"
version: "0.0.0"
type: "package" # One of: package, mode, mcp, prompt
sourceUrl: "https://url.to/source-repository" # Optional
binaryUrl: "https://url.to/binary.zip"
binaryHash: "SHA256-of-binary"
binarySource: "https://proof.of/source" # Optional, proof-of-source for the binary (tag/hash reference, build job, etc)
tags:
    - tag1
    - tag2
author: "your name" # optional
authorUrl: "http://your.profile.url/" # optional
```

### Localization Support

You can provide metadata in multiple languages by using locale-specific files:

**Important Notes on Localization:**

- Only files with the pattern `metadata.{locale}.yml` are supported
- The Marketplace will display metadata in the user's locale if available
- If the user's locale is not available, it will fall back to English
- The English locale (`metadata.en.yml`) is required as a fallback
- Files without a locale code (e.g., just `metadata.yml`) are not supported

### Configurable Support

Powered with [**`Roo Rocket`**](https://github.com/NamesMT/roo-rocket), the registry supports configurable items like:
+ `mcp` with access token inputs.
+ `mode` / `prompt` with feature flags.
+ And further customizations that a creator can imagine.
  + E.g: a `package` could prompt you for the location of its context folder.

## Contributing Process

To contribute your package to the official repository, follow these steps:

### 1. Fork the Repository

1. Visit the official Roo Code Packages repository: [https://github.com/RooVetGit/Roo-Code-Marketplace](https://github.com/RooVetGit/Roo-Code-Marketplace)
2. Click the "Fork" button in the top-right corner
3. This creates your own copy of the repository where you can make changes

### 2. Clone Your Fork

Clone your forked repository to your local machine:

```bash
git clone https://github.com/YOUR-USERNAME/Roo-Code-Marketplace.git
cd Roo-Code-Marketplace
```

### 3. Create Your Item

1. Create a new directory for your item with an appropriate name
2. Add the required metadata files (and subitem directories for `package`)
3. Follow the structure and format described above
4. Add `sourceUrl` that points to a repository or post with info/document for the item.

Example of creating a simple package:

```bash
mkdir -p my-package/modes/my-mode
touch my-package/metadata.en.yml
touch my-package/README.md
touch my-package/modes/my-mode/metadata.en.yml
```

### 4. Test Your Package

Before submitting, test your package by adding your fork as a custom source in the Marketplace:

1. In VS Code, open the Marketplace
2. Go to the "Settings" tab
3. Click "Add Source"
4. Enter your fork's URL (e.g., `https://github.com/YOUR-USERNAME/Roo-Code-Marketplace`)
5. Click "Add"
6. Verify that your package appears and functions correctly

### 5. Commit and Push Your Changes

Once you're satisfied with your package:

```bash
git add .
git commit -m "Add my-package with mode component"
git push origin main
```

### 6. Create a Pull Request

1. Go to the original repository: [https://github.com/RooVetGit/Roo-Code-Marketplace](https://github.com/RooVetGit/Roo-Code-Marketplace)
2. Click "Pull Requests" and then "New Pull Request"
3. Click "Compare across forks"
4. Select your fork as the head repository
5. Click "Create Pull Request"
6. Provide a clear title and description of your package
7. Submit the pull request

### 7. Review Process

After submitting your pull request:

1. Maintainers will review your package
2. They may request changes or improvements
3. Once approved, your package will be merged into the main repository
4. Your package will be available to all users of the Marketplace

## Best Practices

- **Clear Documentation**: Include detailed documentation in your README.md
- **Descriptive Metadata**: Write clear, informative descriptions
- **Appropriate Tags**: Use relevant tags to make your package discoverable
- **Testing**: Thoroughly test your package before submitting
- **Localization**: Consider providing metadata in multiple languages
- **Semantic Versioning**: Follow semantic versioning for version numbers
- **Consistent Naming**: Use clear, descriptive names for components

## Example package metadatas

### Data Science Toolkit

Here's an example of a data science package:

**data-science-toolkit/metadata.en.yml**:

```yaml
name: "Data Science Toolkit"
description: "A comprehensive collection of tools for data science workflows"
version: "1.0.0"
type: "package"
tags:
    - data
    - science
    - analysis
    - visualization
    - machine learning
```

**data-science-toolkit/modes/data-scientist-mode/metadata.en.yml**:

```yaml
name: "Data Scientist Mode"
description: "A specialized mode for data science tasks"
version: "1.0.0"
type: "mode"
tags:
    - data
    - science
    - analysis
```

**data-science-toolkit/prompts/data-cleaning/metadata.en.yml**:

```yaml
name: "Data Cleaning Prompt"
description: "A prompt for cleaning and preprocessing datasets"
version: "1.0.0"
type: "prompt"
tags:
    - data
    - cleaning
    - preprocessing
```

---

# Adding Custom Marketplace Sources

The Marketplace allows you to extend its functionality by adding custom sources. This guide explains how to set up and manage your own Marktplace repositories to access additional components beyond the default offerings.

## Setting up a Marketplace Source Repository

A Marketplace source repository is a Git repository that contains Marketplace items organized in a specific structure. You can create your own repository to host custom packages:

### Repository Requirements

1. **Proper Structure**: The repository must follow the required directory structure
2. **Valid Metadata**: Each package must include properly formatted metadata files
3. **Git Repository**: The source must be a Git repository accessible via HTTPS

### Building your registry repository

#### Start from a sample registry repository

Check the branches of the [**rm-samples**](https://github.com/NamesMT/rm-samples) repository here.

#### Creating a New Repository

1. Create a new repository on GitHub, GitLab, or another Git hosting service
2. Initialize the repository with a README.md file
3. Clone the repository to your local machine:

```bash
git clone https://github.com/your-username/your-registry-repo.git
cd your-registry-repo
```

4. Create the basic registry structure:

```bash
mkdir -p packages modes mcps prompts
touch metadata.en.yml
```

5. Add repository metadata to `metadata.en.yml`:

```yaml
name: "Your Repository Name"
description: "A collection of custom packages for Roo Code"
version: "1.0.0"
```

6. Commit and push the initial structure:

```bash
git add .
git commit -m "Initialize package repository structure"
git push origin main
```

## Adding Sources to Roo Code

Once you have a properly structured source repository, you can add it to your Roo Code Marketplace as a source:

### Default Package Source

Roo Code comes with a default package source:

- URL: `https://github.com/RooVetGit/Roo-Code-Marketplace`
- This source is enabled by default, and anytime all sources have been deleted.

### Adding a New Source

1. Open VS Code with the Roo Code extension
2. Navigate to the Marketplace
3. Switch to the "Sources" tab
4. Click the "Add Source" button
5. Enter the repository URL:
    - Format: `https://github.com/username/repository.git`
    - Example: `https://github.com/your-username/your-registry-repo.git`
6. Click "Add" to save the source

### Managing Sources

The "Sources" tab provides several options for managing your registry sources:

1. **Remove**: Delete a source from your configuration
2. **Refresh**: Update the item list from a source - this is forced git clone/pull to override local caching of data

### Source Caching and Refreshing

Marketplace sources are cached to improve performance:

- **Cache Duration**: Sources are cached for 1 hour (3600000 ms)
- **Force Refresh**: To force an immediate refresh of a source:
    1. Go to the "Sources" tab
    2. Click the "Refresh" button next to the source you want to update
    3. This will bypass the cache and fetch the latest data from the repository

### Troubleshooting Sources

If a source isn't loading properly:

1. Check that the repository URL is correct
2. Ensure the repository follows the required structure
3. Look for error messages in the Marketplace interface
4. Try refreshing the sources list
5. Disable and re-enable the source

## Creating Private Sources

For team or organization use, you might want to create private sources:

### Private Repository Setup

1. Create a private repository on your Git hosting service
2. Follow the same structure requirements as public repositories
3. Set up appropriate access controls for your team members

### Authentication Options

To access private repositories, you may need to:

1. Configure Git credentials on your system
2. Use a personal access token with appropriate permissions
3. Set up SSH keys for authentication

### Organization Best Practices

For teams and organizations:

1. Designate maintainers responsible for the source
2. Establish quality standards for contributed items and packages
3. Create a review process for new additions
4. Document usage guidelines for team members
5. Consider implementing versioning for your items and packages

## Using Multiple Sources

The Marketplace supports multiple sources simultaneously:

### Benefits of Multiple Sources

- Access components from different providers
- Separate internal and external components
- Test new work before contributing them to the main repository
- Create specialized sources for different projects or teams

### Source Management Strategy

1. Keep the default source enabled for core components
2. Add specialized sources for specific needs
3. Create a personal source for testing and development
4. Refresh sources after you've pushed changes to them to get the latest items

---
