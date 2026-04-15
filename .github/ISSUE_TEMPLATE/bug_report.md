name: 🐛 Bug Report
about: Create a report to help us improve the skill logic.
title: "[BUG] "
labels: bug
assignees: ''

body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to fill out this bug report!
  - type: textarea
    id: what-happened
    attributes:
      label: What happened?
      description: Also tell us, what did you expect to happen?
      placeholder: Tell us what you see...
    validations:
      required: true
  - type: dropdown
    id: assistant
    attributes:
      label: AI Assistant Used
      options:
        - Claude (Desktop/Web)
        - Cursor (.mdc)
        - Windsurf
        - Other (please specify)
  - type: textarea
    id: repro
    attributes:
      label: Steps to Reproduce
      description: Provide the command/context that triggered the bug.
      placeholder: |
        1. Ran /wsa:init
        2. Provided response X
        3. Skill failed at step Y
  - type: textarea
    id: logs
    attributes:
      label: Relevant Logs or Context
      description: Please copy/paste any relevant output.
      render: markdown
