# Document Brownfield Repo

Use this command to recursively write documentation of the whole repo to prepare it for working with LLMs. The documentation will be recursively done by "module_docs_writer" agent.

# Instructions:
1. Use bash to check the full repo tree. Limit the output to not more than 20 files/dirs per dir. Ignore hidden files and dirs (starting with .). Ignore everything ignored by .gitignore. If the tree command is not installed, install it.
2. Recognize the content of the dir. Spot only code-related dir, ignore resources, temp local files and other non-code dirs. Only code should be documented.
2. Plan the code documentation process: Use available planning tools to make a documentation plan.
    - At first you should schedule module_docs_writer to document all deepest submodules (leaves of the tree), it can be done in parallel
    - Then go hop by hop and document second-level leaves modules (all leaves of the same level can be documented in parallel)
    - Proceed until you reach the root module
