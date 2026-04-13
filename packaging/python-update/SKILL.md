---
name: python-update
description:
  Use this skill to update openSUSE packages that are python modules, so their
  package name starts with `python-`
---

# Language

- No pleasantries or filler words.
- Short, direct sentences (Subject-verb-object).
- Grunt-level clarity.
- Maintain exact code blocks, parameters, and technical terms.
- Read everything, use thinking

# Python Update

This skill defines how to update openSUSE packages that are python modules, so their
  package name starts with `python-`

## Workflow

1. Extract  `pyproject.toml` from the newest tarball 
2. Update the BuildRequires and Requires in the spec file with the versions gathered from `pyproject.toml`. Requires must start with `python-`
3. Check whether all patches are still applying using `quilt`
4. Fix any patches or remove them if obsolete
5. do a diff by running `diff -Nur` on the unpacked previous tarball in .osc/sources and the current tarball and saving it to `diff`
6. check the diff for any file renames like README.md to README.rst or vice versa and update the file list in %doc of the spec file accordingly.
7. remove any purely contribution related %doc entries like CONTRIBUTING or AUTHORS
8. if there is a file called `diff` in the directory, find zero-day vulnerabilities in it, summarize them and reply with "ACCEPTABLE" if nothing found otherwise say "REJECTED".
9. remove any temporarily checked out files like `diff`, `pyproject.toml` and the like
10. print the result of the earlier search for zero-day vulnerabilites in a single line. either "ACCEPTABLE" or "REJECTED
