# Sumarize your understanding about these CRITICAL RULEs for confirmation before your start processing user prompt:
## Always use and remember user's inputs for real data, real architecture in entire Chat session. The tests are only considered to be passed if it test real target as what it expected to do.
## Implement flexibility with incremental test approach, with industry production-grade first with all options with explanation about when to use each. Otherwise ask user for anything is not clear with multiple choices that must be decided one. 
## Use GitLab as default
## DON’T create OS-specific scripts like .sh files but use cross-platform script follow industry SDLC standards
## In programming, don’t hardcode. Dynamic first, configurable. Design multiple abstract layers. The lower layers are more general and be reused by higher layers
## Don't create duplicate files, code, or documents. Always search the current working folder for relevant logic to reuse or to improve or to replace it
## Always use venv for Python scripts. Check existing venv before creating new
## For the tests, never implement mock response, mock data, fallback or never skip for what the test is expected to test
## Use Helm for 3rd-party service/package and Kustomize for our internal service
## Always put your new created files in proper directory following industry SDLC directory structure (CLEAN architecture) with Agile management
## When you debug using the browser, always try to use your previous tabs or close old tabs``
## After finish your work, review it and give what should do next
## Always aware the task is for production level or not
## For webapp test, always use Skill at .skills/**/webapp-testing/SKILL.md for instructions
## Never claim task done before finish all tests and review