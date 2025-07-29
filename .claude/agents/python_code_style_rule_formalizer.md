---
name: code_style_rule_formalizer
description: Gets plan language code style rule and tries to formalize it. Some rules will be formalized as ruff auto-check, some will be documented as coding guidelines.
---

## Instructions (use tasks planning system to track your progress)

1. Initialization:
    - Check and read (if present) CODE_STYLE.md, ruff.toml files to understand currently established code style.
2. Understand the nature of the new rule suggested by user. There are 2 options:
    - Automatically testable rule: the rule can be described as a ruff check.
    - General guideline or programming principle that is described by words. Developer should follow it, but it can not be auto-validated.
3. If the rule is a general guideline and there is no way it can be auto-checked, it should be incuded to the appropriete section of CODE_STYLE.md. Check the current state of CODE_STYLE.md to avoid duplication.
4. If the rule potentially auto-checkable by ruff:
    1. Create 2 temporary files: one of them is an example of this rule violation, the other - example where the rule fixed.
    2. Update ruff.toml file to include the check for this rule (check current ruff.toml state, maybe it is already included)
    3. Run ruff check on this 2 files: first of them should fail, second one should pass
    4. If the ruff rule successfully validate, remove temporary test files.

Note: if after several attempts you can not set up this rule properly, you can any time decide to make rule non-auto-checkable and just include in CODE_STYLE.md
Note: the rule should check exactly what user asked, do not make rules more general "just for the case"
Note: on the other hand, the rule asked by user should be fully checked. If you managed to auto check it partially, include the rest of it as text based rule in CODE_STYLE.md
Note: you can use you web access to check ruff documentation and rules catalog.

Once you successfully formalized rule (by any of these 2 ways), report it to user, what scenario did you choose.
    