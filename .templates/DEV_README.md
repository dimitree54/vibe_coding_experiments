# Development information

## Dependencies

### Outside dependencies
What 3rd party libraries used, if available link to docs (llms.txt). What library version expected? How is it used (in short, no need to list all usages). Provide a list of the most important dependencies with their version (like requirements.txt, but with an extra description)

### Inter module dependencies

#### This module depends on
What other modules of this repo used as dependencies? Make a full list. Provide path to them (from the repo root) and why they are needed and how used.

For each such dependency, go to dependancy module and 
- If it contains README.md, add current module to "Other modules depending on this module" section of this dependency module README.md
- If this module does not contain README.md, create it, but with only section "Other modules depending on this module" with current module as the only entry.

#### Other modules depending on this module
If some module decides to depend on this one, it should update this file and include itself to this list. On creation of module, this section contains empty list.

Important: Do not assume some dependencies. It is not a "modules potentially depending", not "modules that will be depending", it is a full list of modules is 100% known that they depend on current module. To make this list, search for current module imports across the repo.

## QA

A detailed description of QA strategies used for developing this module.

### Auto-Tests
Path to tests dir of this module, short description of test files and functions in it (a list of functionality tested). Describe what integration tests included.

### Not covered by tests
If some functionality not covered by tests, list it here with short description why it is decided not to test it.

### Manual-Testing scripts
If something can not be auto tested, describe how it can be tested manually: testing script and expected behaviour.

## Requirements to this module
During this module development, what requirements were stated? Make a detailed list of requirements explicitly requested by PRDs. If the module had several iterations of development, include an aggregation of all requirements from all iterations. It might be any requirements, for example
- the function X should work no more than N seconds
- there should be a rainbow on the B button
- the module should use T technology
...

Note: the only source of requirements is PRDs, do not assume any non explicitly requrested requirements based on the code. If you are documenting the brownfield code, leave requriments list empty.
