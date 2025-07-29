# Document Brownfield Repo

Use this command to recursively write documentation of the whole repo to prepare it for working with LLMs. The documentation will be recursively done by "module_docs_writer" agent.

# Instructions:
1. Read .gitignore file
2. Run "tree -I '.*'" plus also exclude all contents of .gitignore
3. Recognize the content of the dir. Spot only code-related dir, ignore resources, temp local files and other non-code dirs. Only code should be documented.
4. Plan the code documentation process: Use available planning tools to make a documentation plan.
    - At first you should schedule module_docs_writer to document all deepest submodules (leaves of the tree).
    - Then go hop by hop and document second-level leaves modules
    - Proceed until you reach the root module and all modules documented


Note: leaves of the same level might be documented in parallel, but parent modules documentation is dependent on documentation of all child modules first.
