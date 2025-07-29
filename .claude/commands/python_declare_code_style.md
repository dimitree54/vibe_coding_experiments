# Declare Code Style

This command will guide you through declaring code style the repo should follow and setup auto code style enforcement where possible.

# Instructions:
1. Check and read (if present) CODE_STYLE.md, ruff.toml and flake8 files to understand currently established code style.
2. Ask user, what additional code style rules they want to introduce. Note: rule might be anything, it might be naming convension or formatting standards or requirement to follow some coding principles. Some of these rules are easily verifiable by linters, others just text guidelines for development.
3. Inform user that it is highly recommended to set up tests coverage standards when working with LLM generated code. If it is ok with them, include it as a part of code style. Also notify them that this LLMs coding framework is optimized for usage of ruff linter, because it has --fix mode, so we will try to formalize these code styles as ruff config.
4. Suggest several more rules to include based on the already included. Consider suggesting some popular rules that are known to be useful.
4. Analyze all the rules you discussed and compile all rules into a full list of elementary rules.
5. Use your planning tools to schedule formalization of each individual rule by "python_code_style_rule_formalizer" agent which will decide what to do with each rule

Note: process each rule sequentially, not parallel
