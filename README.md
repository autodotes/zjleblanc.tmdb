# Ansible Collection - zjleblanc.tmdb

The tmdb collection contains modules for automating [The Movie Database](https://www.themoviedb.org/) API.

## Automated collection build 

This repo contains a blueprint for automating your collection builds using GitHub workflows and semantic versioning.

> Semantic versioning refers to the method which uses contents of a commit message (or pull request) to increment the major, minor, or patch component of a product's version.

Below are the important components which enable semantic versioning in this repository:

| Component | Purpose |
| --- | --- |
| [ansible.cfg template](ansible.cfg.publish) | Defines galaxy servers with tokenized values for security which are injected using GitHub secrets at runtime. This determines **where** the collections are published. |
| [galaxy.yml](galaxy.yml) | The galaxy file is used to define metadata about the collection itself - for semantic versioning we tokenize the version value to be set dynamically during the build. |
| [increment-tag.sh](.github/scripts/increment-tag.sh) | This script uses repository tags to determine the current version and processes the associated commit message to properly increment the version. By default, the patch (or z) component will be incremented. Check out the script to understand how major, minor versions are incremented. |
| [publish.yml](.github/workflows/publish.yml) | The workflow brings everything together - dependencies to build are installed, tokens injected, version set, and collection published. The example in this repository is setup for a manual trigger, but you can modify it to run on pull request merge, commit, etc. |


## Installing this collection

You can install the infra.ee_utilities collection with the Ansible Galaxy CLI:

    ansible-galaxy collection install zjleblanc.tmdb

You can also include it in a `requirements.yml` file and install it with `ansible-galaxy collection install -r requirements.yml`, using the format:

<!-- markdownlint-disable MD046 -->
```yaml
---
collections:
  - name: zjleblanc.tmdb
    # If you need a specific version of the collection, you can specify like this:
    # version: ...
```

## Using this collection

### See Also

* [Ansible Using collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html) for more details.

## Licensing

GNU General Public License v3.0 or later.

See [LICENCE](https://www.gnu.org/licenses/gpl-3.0.txt) to see the full text.
