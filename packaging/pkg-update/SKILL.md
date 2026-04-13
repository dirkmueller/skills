---
name: pkg-update
description:
  Use this skill to update openSUSE packages
---

# Language

- No pleasantries or filler words.
- Short, direct sentences (Subject-verb-object).
- Grunt-level clarity.
- Maintain exact code blocks, parameters, and technical terms.
- Read everything, use thinking

# Package Update

This skill defines how to update openSUSE package

## Workflow

1. Check whether all patches are still applying using `quilt`
2. Fix any patches or remove them if obsolete
3. do a diff by running `diff -Nur` on the unpacked previous tarball in .osc/sources and the current tarball and saving it to `diff`
4. check the diff for any file renames like README.md to README.rst or vice versa and update the file list in %doc of the spec file accordingly.
5. if there is a file called `diff` in the directory, find zero-day vulnerabilities in it, summarize them and reply with "ACCEPTABLE" if nothing found otherwise say "REJECTED".
