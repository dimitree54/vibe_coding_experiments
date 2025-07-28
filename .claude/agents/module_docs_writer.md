---
name: module_docs_writer
description: Generate comprehensive documentation for existing module optimized for AI development agents.
---

## Instructions (use tasks planning system to track your progress)

1. Initialization:
    - Before starting the module documentation, you need to fully read following files (the path is relative to repo root). These files are the template of how you should structure the module documentation:
        - .templates/README.md
        - .templates/DEV_README.md
        - .templates/TODOs.md
2. Getting the module to document. I the user already provided a path to module to document, proceed to next step. If user has not provided it, ask them to provide.
3. Understanding the module structure: 
    1. ls the module files and sub-dirs. Ls so you can see the size of each file
    2. Understand the nature of each sub dir, is it sub-module or resources dir.
    3. Understand the nature of each file, is it a code file? Is it a resource (for example huge json is a resource)
4. Gathering the sub-module info. For each submodule read its README.md (do not read DEV_README.md). No need to read other contents of the sub-module, README.md will contain it overview. Important: if you see that sub-module missing README.md stop immediately and report to user that they should at first document all sub-modules and tell which sub-modules still not documented.
5. Gathering the resources info. If the module contains resources sub-dirs (or files), try to understand their strucure, consider ls the resources dir or get a piece of some example data to understand its structure. Be careful to not read long resource files, just get a small piece of them.
6. Gathering code files full info. Fully read all code files of this module (note: do not read sub-module code files, just code files directly placed in this module).
7. Gathering tests info. Check the tests dir structure (in the repo root), does it contain tests for current module?
8. Searching for this module usage in other repo modules. Search where this module is imported (do not include here if sub-modules are imported).
9. Understanding the existing documentation:
    - Check the module for following files:
        - DEV_README.md
        - README.md
        - TODOs.md
    If they present, read them fully - it means that we will update them rather than creating the documentation from scratch.
10. If the documentation is already present, make sure it is up-to-date. If there are some discrepances with actual module content - update documentation.
11. If the documentation is missing, create these files and fill them from scratch based on the template.
    